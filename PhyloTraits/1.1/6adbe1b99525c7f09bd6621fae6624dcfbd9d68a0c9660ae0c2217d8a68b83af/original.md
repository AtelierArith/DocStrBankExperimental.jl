```
ancestralreconstruction(fr::AbstractDataFrame, net::HybridNetwork; kwargs...)
```

Estimate the ancestral traits on a network, given some data at the tips. Uses function [`phylolm`](@ref) to perform a phylogenetic regression of the data against an intercept (amounts to fitting an evolutionary model on the network).

See documentation on [`phylolm`](@ref) and `ancestralreconstruction(obj::PhyloNetworkLinearModel[, X_n::Matrix])` for further details.

Returns an object of type [`ReconstructedStates`](@ref).
