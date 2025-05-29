```
XPRS_OUTPUTLOG
```

This controls the level of output produced by the Optimizer during optimization. (integer)

In the Console Optimizer, `OUTPUTLOG` controls which messages are sent to the screen (`stdout`). When using the Optimizer library, no output is sent to the screen. If the user wishes output to be displayed, they must define a callback function and print messages to the screen themselves. In this case, `OUTPUTLOG` controls which messages are sent to the user output callback.

Default value: `1`

Values: 0 : Turn all output off. Use `XPRS_OUTPUTLOG_NO_OUTPUT` from `xprs.h`. 1 : Print all messages. Use `XPRS_OUTPUTLOG_FULL_OUTPUT` from `xprs.h`. 3 : Print error and warning messages. Use `XPRS_OUTPUTLOG_ERRORS_AND_WARNINGS` from `xprs.h`. 4 : Print error messages only. Use `XPRS_OUTPUTLOG_ERRORS` from `xprs.h`.
