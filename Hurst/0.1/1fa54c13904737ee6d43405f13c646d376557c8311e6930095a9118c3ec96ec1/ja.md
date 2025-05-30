```
generalised_hurst_range(X, τ_range, q_range)
```

系列 `X` の一般化ハースト指数 (GHE) を、範囲 `τ_range` にわたる絶対モーメント `q_range` で計算し、その標準誤差も求めます。

戻り値は `(length(q_range), 2)` の行列で、最初の列には GHE の値が含まれ、2 番目の列には標準誤差が含まれます。

詳細は [`hurst_exponent`](@ref) を参照してください。

# 例

```jldoctest
julia> X = accumulate(+, randn(1000));

julia> q_range = 0.:0.1:1.; tau_range = 1:19;

julia> generalised_hurst_range(X, tau_range, q_range);
```
