```
XPRS_MAXMIPSOL
```

Branch and Bound: This specifies a limit on the number of integer solutions to be found by the Optimizer. (integer)

It is possible that during optimization the Optimizer will find the same objective solution from different nodes. However, `MAXMIPSOL` refers to the total number of integer solutions found, and not necessarily the number of distinct solutions.

Default value: `0`

Domain: 0~+INF
