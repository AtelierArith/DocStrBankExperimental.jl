```
XPRS_PREDOMCOL
```

Presolve: Determines the level of dominated column removal reductions to perform when presolving a mixed integer problem. (integer)

Only binary columns will be checked.

Default value: `-1`

Values: -1 : Automatically determined. 0 : Disabled. 1 : Cautious strategy. 2 : All candidate binaries will be checked for domination.
