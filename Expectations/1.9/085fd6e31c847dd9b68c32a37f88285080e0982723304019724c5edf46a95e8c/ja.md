```
expectation(f::Function, dist::DiscreteUnivariateDistribution, alg::Type{FiniteDiscrete} = FiniteDiscrete; kwargs...) = expectation(dist, alg; kwargs...)(f)
```

（有限）離散一変量分布のための便利な関数です。
