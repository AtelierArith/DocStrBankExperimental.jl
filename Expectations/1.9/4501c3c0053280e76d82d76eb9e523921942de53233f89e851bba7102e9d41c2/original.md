```
expectation(dist::ContinuousUnivariateDistribution, alg::Type{<:QuadratureAlgorithm} = Gaussian; kwargs...) = _expectation(dist, alg; kwargs...)
```

Dispatcher for continuous univariate expectations.
