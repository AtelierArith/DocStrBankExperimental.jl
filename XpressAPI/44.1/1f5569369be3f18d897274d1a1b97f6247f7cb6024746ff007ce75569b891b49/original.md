```
XPRS_CALLBACKCHECKTIMEDELAY
```

Minimum delay in milliseconds between two consecutive executions of the CHECKTIME callback in the same solution process (integer)

Default value: `0`

Values: 0 : Callback delay is disabled - the callback is executed every time; n>0 : Callback invocation is suppressed if less than n milliseconds have passed since the last invocation.
