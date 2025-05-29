```
KahanMean(; T=Float64, weight=EqualWeight())
```

単変量平均を追跡します。更新のために補償項を使用します。

# 注意

これはほとんどの場合、[`Mean`](@ref) よりも正確ですが、[`KahanSum`](@ref) の保証は適用されません。[`merge!`](@ref) にはいくつかの精度の問題がある可能性があります。

# 更新

$$
μ = (1 - γ) * μ + γ * x
$$

# 例

```
@time fit!(KahanMean(), randn(10^6))
```
