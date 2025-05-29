```
XPRS_MAXCHECKSONMAXCUTTIME
```

This control is intended for use where optimization runs that are terminated using the MAXCUTTIME control are required to be reproduced exactly. (integer)

This control is necessary because of the inherent difficulty in terminating algorithmic software in a consistent way using temporal criteria. The control value relates to the number of times the optimizer checks the `MAXCUTTIME` criterion up to and including the check when the termination of cutting was activated. To use the control the user first must obtain the value of the CHECKSONMAXCUTTIME attribute after the run returns. This attribute value is the number of times the optimizer checked the `MAXCUTTIME` criterion during the last call to the optimization routine XPRSmipoptimize. Note that this attribute value will be negative if the optimizer terminated cutting on the `MAXCUTTIME` criterion. To ensure accurate reproduction of a run the user should first ensure that `MAXCUTTIME` is set to its default value or to a large value so the run does not terminate again on `MAXCUTTIME` and then simply set the control `MAXCHECKSONMAXCUTTIME` to the absolute value of the `CHECKSONMAXCUTTIME` value.

Default value: `0`

Values: 0 : Not active. n>0 : The number of times the optimizer should check the `MAXCUTTIME` criterion before triggering a termination.
