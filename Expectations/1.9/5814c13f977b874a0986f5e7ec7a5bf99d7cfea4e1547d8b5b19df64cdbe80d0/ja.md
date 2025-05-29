```
expectation(dist::ContinuousUnivariateDistribution, nodes, alg::Type{<:ExplicitQuadratureAlgorithm} = Trapezoidal; kwargs...)  = _expectation(dist, nodes, alg; kwargs...)
```

ユーザー定義ノードを持つ分布のディスパッチャー。
