```julia
struct PolarPolar{T1<:(IncrementalInference.SamplableBelief), T2<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractRelativeMinimize
```

2つの`Polar`変数間の`IIF.SamplableBelief`の線形オフセット因子。
