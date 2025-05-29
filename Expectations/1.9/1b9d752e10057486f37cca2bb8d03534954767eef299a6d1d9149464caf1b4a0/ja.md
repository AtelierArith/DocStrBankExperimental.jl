```
expectation(f::Function, dist::ContinuousUnivariateDistribution, nodes::AbstractArray, alg::Type{<:ExplicitQuadratureAlgorithm} = Trapezoidal; kwargs...) = expectation(dist, nodes, alg; kwargs...)(f)
```

ユーザーが提供したノードを持つ連続一変数分布のための便利な関数です。
