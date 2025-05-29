```julia
struct Prior{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Default prior on all dimensions of a variable node in the factor graph.  `Prior` is not recommended when non-Euclidean dimensions are used in variables.
