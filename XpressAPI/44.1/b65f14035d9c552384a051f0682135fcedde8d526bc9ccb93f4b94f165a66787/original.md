```
XPRS_MIPRELSTOP
```

Branch and Bound: This determines when the branch and bound tree search will terminate. (double)

Branch and bound tree search will stop if: |`MIPOBJVAL - BESTBOUND`| `<=` `MIPRELSTOP` x max(|`BESTBOUND`|,|`MIPOBJVAL`|) where MIPOBJVAL is the value of the best solution's objective function and BESTBOUND is the current best solution bound. For example, to stop the tree search when a MIP solution has been found and the Optimizer can guarantee it is within 5 of the optimal solution, set `MIPRELSTOP` to 0.05.

Default value: `0.0001`

Domain: [-INF,+INF]
