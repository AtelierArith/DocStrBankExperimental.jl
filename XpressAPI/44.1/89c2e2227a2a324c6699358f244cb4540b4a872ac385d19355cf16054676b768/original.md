```
XPRS_GLOBALLSHEURSTRATEGY
```

When integer-feasible (for MINLP, any solution for NLP) but nonlinear-infeasible solutions are encountered within a global solve, the integer variables can be fixed and a local solver (as defined by the `LOCALSOLVER` control) can be called on the remaining continuous problem. (double)

This control defines the frequency and effort of such local solves.

Default value: `-1`

Values: -1 : Automatic selection of the strategy. 0 : Never run a local solver on a partially fixed solution. 1 : Conservative strategy. 2 : Moderate strategy. 3 : Aggressive strategy.
