```
expectation(f::Function, dist::DiscreteUnivariateDistribution, alg::Type{FiniteDiscrete} = FiniteDiscrete; kwargs...) = expectation(dist, alg; kwargs...)(f)
```

Convenience function for (finite) discrete univariate distributions.
