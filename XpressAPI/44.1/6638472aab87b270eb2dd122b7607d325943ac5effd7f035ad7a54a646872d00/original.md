```
XPRS_BARSOLUTION
```

This determines whether the barrier has to decide which is the best solution found or return the solution computed by the last barrier iteration. (integer)

Default value: `0`

Values: -1 : (callback only: do not save current soulution as the best one). 0 : return the best solution found (in callback: let the barrier decide the current solution is the best or not). 1 : return the last barrier iteration (in callback: save current solution as the best solution so far).
