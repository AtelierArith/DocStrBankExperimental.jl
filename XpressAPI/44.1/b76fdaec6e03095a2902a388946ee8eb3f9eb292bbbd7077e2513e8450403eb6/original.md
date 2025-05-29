```
XPRS_MIPABSCUTOFF
```

Branch and Bound: If the user knows that they are interested only in values of the objective function which are better than some value, this can be assigned to `MIPABSCUTOFF`. (double)

This allows the Optimizer to ignore solving any nodes which may yield worse objective values, saving solution time. When a MIP solution is found a new cut off value is calculated and the value can be obtained from the CURRMIPCUTOFF attribute. The value of CURRMIPCUTOFF is calculated using the `MIPRELCUTOFF` and `MIPADDCUTOFF` controls.

Default value: `1.0E+40` (for minimization problems); `-1.0E+40` (for maximization problems).

Domain: [-INF,+INF]
