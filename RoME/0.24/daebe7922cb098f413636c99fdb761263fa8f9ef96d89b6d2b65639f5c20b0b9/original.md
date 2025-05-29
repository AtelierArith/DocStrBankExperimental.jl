```julia
struct PriorPolar{T1<:(IncrementalInference.SamplableBelief), T2<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Prior belief on any Polar related variable.
