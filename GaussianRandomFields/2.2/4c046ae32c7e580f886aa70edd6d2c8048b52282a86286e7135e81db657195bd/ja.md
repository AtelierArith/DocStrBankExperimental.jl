```
SeparableCovarianceFunction(cov...)
```

`cov`の次元数`length(cov)`の分離可能共分散関数。異方性共分散関数を定義するのに便利で、非分離可能な`KarhunenLoeve`展開が高価すぎる場合に使用します。

# 例

```
julia> SeparableCovarianceFunction(Exponential(0.1), Matern(0.01, 1.0))
2d separable covariance function [ exponential (λ=0.1, σ=1.0, p=2.0), Matérn (λ=0.01, ν=1.0, σ=1.0, p=2.0) ]

```

関連項目: [`CovarianceFunction`](@ref), [`KarhunenLoeve`](@ref)
