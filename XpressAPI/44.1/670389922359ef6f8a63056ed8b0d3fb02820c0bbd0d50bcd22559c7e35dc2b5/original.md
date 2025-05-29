```
XPRS_CHECKSONMAXCUTTIME
```

This attribute is used to set the value of the MAXCHECKSONMAXCUTTIME control. (integer)

Its value is the number of times the optimizer checked the MAXCUTTIME criterion during the last call to the optimization routine XPRSmipoptimize. If a run terminates cutting operations on the `MAXCUTTIME` criterion then the attribute is the negative of the number of times the optimizer checked the `MAXCUTTIME` criterion up to and including the check when the termination was activated. Note that the attribute is set to zero at the beginning of each call to an optimization routine.
