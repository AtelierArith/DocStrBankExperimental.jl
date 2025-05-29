```
SchedulerParameters
```

Parameters for the scheduler adopted from settings by default.

# Elements

  * `titer`: maximum number of iterations (<0: turned off)
  * `lnewinc`: always write iteration log if new incumbent solution
  * `lfreq`: frequency of writing iteration logs (0: none, >0: number of iterations,    -1: iteration 1,2,5,10,20,...)
  * `tciter`: maximum number of iterations without improvement (<0: turned off)
  * `ttime`: time limit [s](<0: turned off)
  * `tctime`: maximum time [s] without improvement (<0: turned off)
  * `tobj`: objective value at which should be terminated when reached (<0: turned off)
  * `checkit`: call `check` for each solution after each method application
  * `log`: if true write all log information, else none
