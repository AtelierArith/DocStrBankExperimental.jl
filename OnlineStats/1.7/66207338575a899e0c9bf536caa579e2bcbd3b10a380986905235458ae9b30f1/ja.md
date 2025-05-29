```
KahanVariance(; T=Float64, weight=EqualWeight())
```

単変量分散を追跡します。より高い精度のために補償項を使用します。

# 注意

これはほとんどの場合、[`Variance`](@ref) よりも正確ですが、[`KahanSum`](@ref) の保証は適用されません。[`merge!`](@ref) は精度の問題を抱える可能性があります。

# 例

```
o = fit!(KahanVariance(), randn(10^6))
mean(o)
var(o)
std(o)
```
