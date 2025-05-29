```
hurst_exponent(X, τ_range)
```

系列 `X` のハースト指数を範囲 `τ_range` にわたって計算し、その標準誤差を求めます。

[Buonocore et al. 2016](https://doi.org/10.1016/j.chaos.2015.11.022) を参照してください。

# 例

```jldoctest
julia> X = accumulate(+, randn(1000));

julia> isapprox(hurst_exponent(X, 1:19)[1], 0.5, atol = 0.1)
true
```
