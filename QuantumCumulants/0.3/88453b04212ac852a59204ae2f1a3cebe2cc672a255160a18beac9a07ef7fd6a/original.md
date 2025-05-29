```
scale(me::IndexedMeanfieldEquations;h)
scale(me::CorrelationFunction;h)
```

Function, that evaluates a given [`MeanfieldEquations`](@ref) or [`CorrelationFunction`](@ref) entity and returns again equations, where indices have been inserted and sums evaluated, regarding the same relations, as done when calculating with oparators using a [`ClusterSpace`](@ref). For this it is considered that all entities in the given (sub)system are acting on the system equivalently.

# Arguments

*`me::IndexedMeanfieldEquations`: A [`MeanfieldEquations`](@ref) entity, which shall be scaled.

# Optional argumentes

*`h`: A HilbertSpace, Vector of Hilbertspaces or Numbers, specifying the specific Hilbertspaces,     that shall be scaled. Does not scale any other Hilbertspace, other than the given ones.
