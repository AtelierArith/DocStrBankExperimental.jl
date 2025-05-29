```
XPRS_QSIMPLEXOPS
```

Controls the behavior of the quadratic simplex solvers. (integer)

Default value: `0`

Values are a bitset: bit 0 : Force traditional primal first phase. bit 1 : Force BigM primal first phase. bit 2 : Force traditional dual first phase. bit 3 : Force BigM dual first phase. bit 4 : Always use artificial bounds in dual. bit 5 : Use original problem basis only when warmstarting the KKT. bit 6 : Skip the primal bound flips for ranged primals (might cause more trouble than good if the bounds are very large). bit 7 : Also do the single pivot crash. bit 8 : Do not apply aggressive perturbation in dual. bit 9 : Applies standard scaling to the KKT system. bit 10 : Do not fall back to using Barrier in case of numerical difficulties with quadratic simplex during a MIP solve. bit 11 : Use primal simplex to solve the phase 1 feasibility problem before applying quadratic primal simplex. bit 12 : Use dual simplex to solve the phase 1 feasibility problem before applying quadratic primal simplex. bit 13 : Use barrier algorithm to solve the phase 1 feasibility problem before applying quadratic primal simplex. bit 14 : Use partial pricing. bit 15 : Use full pricing. bit 16 : Perform cleanup if a superbasic solution is provided for warm-start.
