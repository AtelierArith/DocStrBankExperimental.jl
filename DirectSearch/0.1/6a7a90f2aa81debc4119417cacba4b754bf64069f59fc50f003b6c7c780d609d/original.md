```
SetOpportunisticEvaluation(p::DSProblem; opportunistic::Bool=true)
```

Set/unset opportunistic evaluation (enables by default).

When using opportunistic evaluation the first allowable evaluated point with an improved cost is set as the new incumbent solution. If using progressive barrier constraints this point may be infeasible.
