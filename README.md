# utl-altair-slc-summary-statistics-on-employees-of-the-maynard-corporation-using-a-text-file
RE: Altair slc summary statistics on employees of the maynard corporation using a text file
    %let pgm=utl-altair-slc-summary-statistics-on-employees-of-the-maynard-corporation-using-a-text-file;

    %stop_submission;

    RE: Altair slc summary statistics on employees of the maynard corporation using a text file

    Too long to post to a listserv, see github
    github
    https://github.com/rogerjdeangelis/utl-altair-slc-summary-statistics-on-employees-of-the-maynard-corporation-using-a-text-file

    community.altair.com
    https://community.altair.com/discussion/39626/altair-monarch-exercise-1-employ#latest

    CONTENTS

    1 Parse text file
    2 How many employees work at the Maynard Corporation?
      What is the Average (AVG) Salary for All Employees?

    3 How many employees are in each department?
      What is the Average (AVG) Salary by Dept?

    4 What are the top 5 Zip Codes where Employees reside?


    /*****************************************************************************************************/
    /* INPUT                | PROCESS                                 | OUTPUT                           */
    /* -----                | -------                                 | ------                           */
    /* 1 PARSE EMPLOT.TXT   |                                         |                                  */
    /*                      |                                         |                                  */
    /* d:\txt\employ.txt    |libname workx "d:/wpswrkx";              |  WORKX.PARSE                     */
    /*                      |                                         |                                  */
    /*                      | data workx.parse;                       |  WORKX.PARSE                     */
    /*                      |                                         |                                  */
    /*                      | infile "d:\txt\employ.txt";             |  Obs  SALARY  ZIP   DEPT         */
    /*                      |                                         |                                  */
    /*                      | informat firstname  lastname  street    |     1   37800 37800 Processing   */
    /*                      |          city  state  zip  hiredate     |     2   47400 47400 Shipping     */
    /*                      |          sex  dept  salry $32.;         |     3   33500 33500 Marketing    */
    /*                      |                                         |     4   39500 39500 Shipping     */
    /*                      | input firstname & lastname & street &   |     5   39600 39600 Accounting   */
    /*                      |        city & state & zip &             |    ..                            */
    /*                      |        hiredate & sex & dept & salry;   |    96   57300 57300 Processing   */
    /*                      |                                         |    97   27500 27500 Accounting   */
    /*                      | salary=input(salry,?? 11.);             |    98   54800 54800 Marketing    */
    /*                      | if not missing (salary);                |    99   57000 57000 Marketing    */
    /*                      |                                         |   100   25300 25300 Production   */
    /*                      | keep dept salary zip;                   |                                  */
    /*                      | run;quit;                               |                                  */
    /*                      |                                         |                                  */
    /*                      | proc print data=workx.parse;            |                                  */
    /*                      | run;quit;                               |                                  */
    /* ---------------------------------------------------------------|----------------------------------*/
    /* 2 HOW MANY EMPLOYEES WORK AT THE MAYNARD CORPORATION?          |                                  */
    /*   WHAT IS THE AVERAGE (AVG) SALARY FOR ALL EMPLOYEES?          |                                  */
    /*                      | proc sql;                               |                                  */
    /*                      | select                                  |  DEPT       Employees    Salary  */
    /*                      |   dept length=18                        |  ------------------------------  */
    /*                      |  ,count(*)    as Total_Employees        |  Accounting        12  40416.67  */
    /*                      |  ,avg(salary) as Average_Salary         |  Marketing         26  52103.08  */
    /*                      | from                                    |  Processing        28  43628.57  */
    /*                      |    workx.parse                          |  Production        12  33166.67  */
    /*                      | group                                   |  Shipping          22  32209.09  */
    /*                      |   by dept                               |                                  */
    /*                      | ;quit;                                  |                                  */
    /*----------------------------------------------------------------|----------------------------------*/
    /* 4 WHAT ARE THE TOP 5 ZIP CODES WHERE EMPLOYEES RESIDE?         |                                  */
    /*                      |                                         |                                  */
    /*                      | proc sql;                               |              Zipcode_            */
    /*                      |  reset                                  |              Zipcode_            */
    /*                      |    outobs=5;                            |  --------------------            */
    /*                      |  select                                 |  01776             20            */
    /*                      |    zip length=6                         |  01803             14            */
    /*                      |   ,count(*) as Zipcode_count            |  01742              6            */
    /*                      | from                                    |  01754              6            */
    /*                      |    workx.parse                          |  01853              6            */
    /*                      | group                                   |                                  */
    /*                      |    by zip                               |                                  */
    /*                      | order                                   |                                  */
    /*                      |    by Zipcode_count descending          |                                  */
    /*                      | ;quit;                                  |                                  */
    /*****************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
