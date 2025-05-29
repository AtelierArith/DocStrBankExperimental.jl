```
midcov(X, [Y]; c=9)
```

二つのベクトル間のバイウェイトミッド共分散を計算します。ベクトルが一つだけ提供された場合、バイウェイトミッド分散が計算されます。

$$
\hat{\sigma}_{xy} = \frac{\sum_{u_i^2 \le 1,v_i^2 \le 1}{(x_i - \bar{x})(1 - u_i^2)^2(y_i - \bar{y})(1 - v_i^2)^2}}{\sum_{u_i^2 \le 1}{(1 - u_i^2)(1 - 5u_i^2)}\sum_{v_i^2 \le 1}{(1 - v_i^2)(1 - 5v_i^2)}}
$$

!!! warning
    `NaN` および `Inf` は共分散計算で除去できないため、これらが存在する場合、返される値は `NaN` になります。これを防ぐために、非有限データに対して値を補完することを検討してください。


# 例

```jldoctest
julia> X = 10 .* randn(rng, 1000, 2) .+ 50;


julia> midcov(X[:, 1], X[:, 2])
-1.058463590812247

julia> midcov(X[:, 1]) ≈ midvar(X[:, 1])
true

julia> X[3, 2] = NaN;


julia> midcov(X[:, 1], X[:, 2])
NaN
```

# 参考文献

1. [NIST: biweight midcovariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidc.htm)

# 関連項目

[`scale`](@ref), [`midvar`](@ref), [`midcor`](@ref)
