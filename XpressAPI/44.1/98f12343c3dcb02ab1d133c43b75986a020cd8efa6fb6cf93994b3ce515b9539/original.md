```
XPRS_MIPABSSTOP
```

Branch and Bound: The absolute tolerance determining whether the tree search will continue or not. (double)

It will terminate if |`MIPOBJVAL - BESTBOUND`| `<=` `MIPABSSTOP` where MIPOBJVAL is the value of the best solution's objective function, and BESTBOUND is the current best solution bound. For example, to stop the tree search when a MIP solution has been found and the Optimizer can guarantee it is within 100 of the optimal solution, set `MIPABSSTOP` to 100.

Default value: `0.0`

Domain: [-INF,+INF]
