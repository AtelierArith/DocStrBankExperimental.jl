```
expectation(f::Function, dist::ContinuousUnivariateDistribution, nodes::AbstractArray, alg::Type{<:ExplicitQuadratureAlgorithm} = Trapezoidal; kwargs...) = expectation(dist, nodes, alg; kwargs...)(f)
```

Convenience function for continuous univariate distributions with user-supplied nodes.
