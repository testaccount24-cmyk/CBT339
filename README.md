# CBT339
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 339 IS FROM E.F. MAC DONALD MOTIVATION FROM DAYTON OHIO.  *   FILE 339
//*           THIS PROGRAM IS A JES2/SP1.3.6 (FMID HJE1367) AND A   *   FILE 339
//*           JES2/SP2.1.7 (FMID HJE2215) USER EXIT #5 ROUTINE.     *   FILE 339
//*           THERE ARE NO INSTALLATION UNIQUE CONSIDERATIONS       *   FILE 339
//*           EXCEPT THAT THE COMMANDS "$JC", "$JL", "$JM" AND      *   FILE 339
//*           "$JD" ARE NOT BEING USED FOR ANYTHING ELSE.  NO       *   FILE 339
//*           CHANGES TO JES2 CODE ARE REQUIRED.                    *   FILE 339
//*                                                                 *   FILE 339
//*             1.  CANCEL ALL JOES (JOB OUTPUT ELEMENTS) OF A      *   FILE 339
//*                 SPECIFIED JOB IN A SPECIFIED SYSOUT CLASS.      *   FILE 339
//*                 SIMILAR TO VS1 "C JOBNAME,OUT=X" EXAMPLES:      *   FILE 339
//*                                                                 *   FILE 339
//*                    $JCJ175,Q=D (CANCEL ALL SYSOUT=D JOES OF     *   FILE 339
//*                                J175)                            *   FILE 339
//*                                                                 *   FILE 339
//*                    $JC'MYJOB',Q=E (CANCEL ALL SYSOUT=E JOES OF  *   FILE 339
//*                                   JOBNAME "MYJOB")              *   FILE 339
//*                                                                 *   FILE 339
//*                 THE OPERAND "Q=" IS REQUIRED; USE JES2 "$C"     *   FILE 339
//*                 COMMAND TO CANCEL ALL OUTPUT OF A JOB.          *   FILE 339
//*                                                                 *   FILE 339
//*             2.  LIST ALL JOES IN SYSOUT CLASS ORDER.            *   FILE 339
//*                                                                 *   FILE 339
//*                 LIST MAY BE RESTRICTED TO A SELECTED CLASS, OR  *   FILE 339
//*                 ALL CLASSES EXCEPT A SELECTED CLASS.  SIMILAR   *   FILE 339
//*                 TO THE VS1 "SO" COMMAND.  EXAMPLES:             *   FILE 339
//*                                                                 *   FILE 339
//*                    $JL      (LIST ALL JOES IN SYSOUT CLASS      *   FILE 339
//*                              ORDER)                             *   FILE 339
//*                    $JL,Q=Z  (LIST ALL JOES IN SYSOUT QUEUE Z)   *   FILE 339
//*                    $JL,Q=-P (LIST ALL JOES EXCEPT THOSE IN      *   FILE 339
//*                              SYSOUT QUEUE P)                    *   FILE 339
//*                                                                 *   FILE 339
//*                 EACH SELECTED JOE IS LISTED IN THE FOLLOWING    *   FILE 339
//*                 FORMAT :                                        *   FILE 339
//*                                                                 *   FILE 339
//*                 JNNNN JJJJJJJJ C I.I.I FORM  X/Y P=NNN          *   FILE 339
//*                 LLLLLLLLL WHERE JNNNN IS THE JES2 JOB NUMBER    *   FILE 339
//*                 (J175, S3968, ETC.), JJJJJJJJ IS THE JOBNAME,   *   FILE 339
//*                 I.I.I IS THE JOE ID, FORM IS THE FORM NUMBER,   *   FILE 339
//*                 FCB IS THE FCB NAME, "X" IS "Y" IF THE DEST IS  *   FILE 339
//*                 LOCAL, "Y" IS "Y" IF THE JOE IS SELECTABLE AND  *   FILE 339
//*                 THE *JOB* IS NOT HELD, "Y" IS "N" IF THE JOE IS *   FILE 339
//*                 NOT SELECTABLE, "Y" IS "H" IF THE JOB IS HELD,  *   FILE 339
//*                 "NNN" IS THE PRIORITY OF THE JOE (NOT THE JOB), *   FILE 339
//*                 AND LLLLLLLLL IS THE JOE LINECOUNT.  TO LIST    *   FILE 339
//*                 ALL JOES OF A PARTICULAR JOB, USE THE JES2      *   FILE 339
//*                 "$L...,ALL" COMMAND.                            *   FILE 339
//*                                                                 *   FILE 339
//*             3.  MOVE THE JOES OF A SELECTED JOB FROM A SELECTED *   FILE 339
//*                 SYSOUT CLASS TO A DIFFERENT SELECTED SYSOUT     *   FILE 339
//*                 CLASS.  SIMILAR TO VS1 "E                       *   FILE 339
//*                 JOBNAME,CLASS=X,OUT=Y".  EXAMPLES:              *   FILE 339
//*                                                                 *   FILE 339
//*                    $JMJ175,FROMQ=X,TOQ=Y (MOVE J175 SYSOUT=X    *   FILE 339
//*                                           JOES TO SYSOUT=Y)     *   FILE 339
//*                                                                 *   FILE 339
//*                    $JM'MYJOB',TOQ=C,FROMQ=G (MOVE JOBNAME       *   FILE 339
//*                                              "MYJOB" SYSOUT=G   *   FILE 339
//*                                              JOES TO SYSOUT=C)  *   FILE 339
//*                                                                 *   FILE 339
//*                 TO MOVE *ALL* JOES OF A JOB TO A SELECTED       *   FILE 339
//*                 SYSOUT CLASS, USE THE JES2 "$TO" COMMAND.       *   FILE 339
//*                                                                 *   FILE 339
//*             4.  DISPLAY THE CURRENT JULIAN DATE.  THIS IS       *   FILE 339
//*                 INTENDED FOR USE WITH THE JES2 AUTOMATIC        *   FILE 339
//*                 COMMAND FACILITY TO DATESTAMP HARDCOPY LOGS.    *   FILE 339
//*                 FORMAT IS "$JD"; NO OPERANDS.                   *   FILE 339
//*                                                                 *   FILE 339
//*          THESE COMMANDS DO NOT ATTEMPT TO DUPLICATE             *   FILE 339
//*          FUNCTIONS WHICH CAN USUALLY BE ACCOMPLISHED WITH A     *   FILE 339
//*          SINGLE JES2 COMMAND.  THIS PROGRAM CHECKS FOR SOME     *   FILE 339
//*          COMMON ERRORS SUCH AS VERIFICATION OF TYPE OF JOB      *   FILE 339
//*          ON REQUESTS BY JOB NUMBER (JOB/STC/TSU), DUPLICATE     *   FILE 339
//*          JOBNAME IN THE PPU QUEUE ON REQUESTS BY JOB NAME,      *   FILE 339
//*          AND JOE BUSY (ON AN OUTPUT DEVICE OR BEING MODIFIED    *   FILE 339
//*          BY A $TO COMMAND).  TO REDUCE OVERHEAD TO A            *   FILE 339
//*          MINIMUM, ALL QUEUE INTEGRITY IS LEFT TO THE $QSUSE     *   FILE 339
//*          SERVICE ROUTINE WHICH IS USED BY THE $#MOD AND         *   FILE 339
//*          $#REM SERVICE ROUTINES, WHICH ARE USED BY THIS         *   FILE 339
//*          PROGRAM (SEE "JES2 LOGIC" LY24-6006).                  *   FILE 339
//*                                                                 *   FILE 339
```
