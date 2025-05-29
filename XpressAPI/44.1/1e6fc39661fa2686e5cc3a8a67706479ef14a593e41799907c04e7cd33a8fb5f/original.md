```
XPRS_SOLTIMELIMIT
```

The maximum time in seconds that the Optimizer will run a MIP solve before it terminates, given that a solution has been found. (double)

As long as no solution has been found, this control will have no effect.

Default value: `1e+20`

Values:

> 0


: If an integer solution has been found, stop MIP search after the given number of seconds, otherwise continue until an integer solution is finally found.
