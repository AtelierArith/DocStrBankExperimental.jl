```
generalised_hurst_exponent(X, τ_range, q)
```

系列 `X` の一般化ハースト指数を、範囲 `τ_range` にわたる絶対モーメント `q` とともに、その標準誤差を計算します。

関連情報は [`hurst_exponent`](@ref) を参照してください。

# 例

```jldoctest
julia> X = accumulate(+, randn(1000));

julia> generalised_hurst_exponent(X, 1:19, 0.5);
```
