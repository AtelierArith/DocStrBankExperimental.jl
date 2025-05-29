```julia
struct MsgPrior{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Message prior on all dimensions of a variable node in the factor graph.

Notes

  * Only temporary existance during CSM operations.
