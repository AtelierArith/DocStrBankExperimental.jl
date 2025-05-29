```
XPRS_MAXCHECKSONMAXTIME
```

This control is intended for use where optimization runs that are terminated using the TIMELIMIT (or the deprecated MAXTIME) control are required to be reproduced exactly. (integer)

This control is necessary because of the inherent difficulty in terminating algorithmic software in a consistent way using temporal criteria. The control value relates to the number of times the optimizer checks the `TIMELIMIT` criterion up to and including the check when the termination was activated. To use the control the user first must obtain the value of the CHECKSONMAXTIME attribute after the run returns. This attribute value is the number of times the optimizer checked the `TIMELIMIT` criterion during the last call to the optimization routine XPRSmipoptimize. Note that this attribute value will be negative if the optimizer terminated on the `TIMELIMIT` criterion. To ensure that a reproduction of a run terminates in the same way the user should first ensure that `TIMELIMIT` is set to its default value or to a large value so the run does not terminate again on `TIMELIMIT` and then simply set the control `MAXCHECKSONMAXTIME` to the absolute value of the `CHECKSONMAXTIME` value.

Default value: `0`

Values: 0 : Not active. n>0 : The number of times the optimizer should check the `TIMELIMIT` (or `MAXTIME`) criterion before triggering a termination.
