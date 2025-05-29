```
phylolm(X::Matrix, Y::Vector, net::HybridNetwork, model::ContinuousTraitEM=BM(); kwargs...)
```

Return a [`PhyloNetworkLinearModel`](@ref) object. This method is called by `phylolm(formula, data, network; kwargs...)`.
