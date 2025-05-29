```
expectation(f::Function, dist::ContinuousUnivariateDistribution, alg::Type{<:QuadratureAlgorithm} = Gaussian; kwargs...) = expectation(dist, alg; kwargs...)(f)
```

Convenience function for continuous univariate distributions.
