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

因子グラフから因子を評価するための単一エントリーポイントであり、複数のディスパッチを使用して正しい `evalPotentialSpecific` 関数を特定します。
