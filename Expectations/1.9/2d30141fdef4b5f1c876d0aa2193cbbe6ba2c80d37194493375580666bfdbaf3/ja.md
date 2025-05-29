```
expectation(f::Function, dist::ContinuousUnivariateDistribution, alg::Type{<:QuadratureAlgorithm} = Gaussian; kwargs...) = expectation(dist, alg; kwargs...)(f)
```

連続一変量分布のための便利な関数です。
