```
apply(cov, pts...)
```

共分散行列を返します。すなわち、点 `x` で評価された共分散関数 `cov` です。

# 例

```jldoctest
julia> exponential_covariance = CovarianceFunction(1, Exponential(1))
1d 指数共分散関数 (λ=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=11)
0.0:0.1:1.0

julia> C = apply(exponential_covariance, pts);

julia> heatmap(C);

julia> whittle_covariance = CovarianceFunction(2, Whittle(1))
2d ウィトル共分散関数 (λ=1.0, σ=1.0, p=2.0)

julia> C = apply(whittle_covariance, pts, pts);

julia> heatmap(C);

```

参照: [`CovarianceFunction`](@ref), [`Exponential`](@ref), [`Whittle`](@ref)
