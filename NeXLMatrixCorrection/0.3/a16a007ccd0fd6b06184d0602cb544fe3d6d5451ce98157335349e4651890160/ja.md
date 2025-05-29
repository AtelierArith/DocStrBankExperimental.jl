```
Iteration(;
    mc::Type{<:MatrixCorrection} = XPP,
    fc::Type{<:FluorescenceCorrection} = ReedFluorescence,
    cc::Type{<:CoatingCorrection} = Coating,
    updater = WegsteinUpdateRule(),
    converged = RMSBelowTolerance(0.00001),
    unmeasured = NullUnmeasuredRule(),
)
```

反復プロセスを定義するために必要な情報を収集します。これには、`MatrixCorrection`および`FLuorescenceCorrection`アルゴリズム、反復`UpdateRule`、`ConvergenceTest`、および`UnmeasuredElementRule`が含まれます。
