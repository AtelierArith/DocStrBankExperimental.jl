```julia
struct PolarPolar{T1<:(IncrementalInference.SamplableBelief), T2<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractRelativeMinimize
```

Linear offset factor of `IIF.SamplableBelief` between two `Polar` variables.
