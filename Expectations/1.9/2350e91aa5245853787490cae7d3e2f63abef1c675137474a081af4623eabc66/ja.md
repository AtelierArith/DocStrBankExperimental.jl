```
expectation(dist::DiscreteUnivariateDistribution, alg::Type{FiniteDiscrete} = FiniteDiscrete; kwargs...) = _expectation(dist, alg; kwargs...)
```

(有限) 離散一変量期待値のためのディスパッチャー。
