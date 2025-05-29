```
XPRS_CHECKSONMAXTIME
```

This attribute is used to set the value of the MAXCHECKSONMAXTIME control. (integer)

Its value is the number of times the optimizer checked the MAXTIME criterion during the last call to the optimization routine XPRSmipoptimize. If a run terminates on the `MAXTIME` criterion then the attribute is the negative of the number of times the optimizer checked the `MAXTIME` criterion up to and including the check when the termination was activated. Note that the attribute is set to zero at the beginning of each call to an optimization routine.
