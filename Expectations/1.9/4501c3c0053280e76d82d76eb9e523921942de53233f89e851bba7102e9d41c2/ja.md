```
expectation(dist::ContinuousUnivariateDistribution, alg::Type{<:QuadratureAlgorithm} = Gaussian; kwargs...) = _expectation(dist, alg; kwargs...)
```

連続一変量期待値のディスパッチャ。
