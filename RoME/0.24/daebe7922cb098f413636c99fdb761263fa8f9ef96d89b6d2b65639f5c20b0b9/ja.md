```julia
struct PriorPolar{T1<:(IncrementalInference.SamplableBelief), T2<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

任意の極に関連する変数に対する事前信念。
