```julia
evalFactor(dfg, fct, solvefor; ...)
evalFactor(
    dfg,
    fct,
    solvefor,
    measurement;
    needFreshMeasurements,
    solveKey,
    variables,
    N,
    inflateCycles,
    nullSurplus,
    dbg,
    skipSolve,
    _slack
)

```

Single entry point for evaluating factors from factor graph, using multiple dispatch to locate the correct `evalPotentialSpecific` function.
