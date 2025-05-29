```
expectation(dist::DiscreteUnivariateDistribution, alg::Type{FiniteDiscrete} = FiniteDiscrete; kwargs...) = _expectation(dist, alg; kwargs...)
```

Dispatcher for (finite) discrete univariate expectations.
