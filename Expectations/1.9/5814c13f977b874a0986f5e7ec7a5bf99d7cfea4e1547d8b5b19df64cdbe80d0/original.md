```
expectation(dist::ContinuousUnivariateDistribution, nodes, alg::Type{<:ExplicitQuadratureAlgorithm} = Trapezoidal; kwargs...)  = _expectation(dist, nodes, alg; kwargs...)
```

Dispatcher for distributions with user-defined nodes.
