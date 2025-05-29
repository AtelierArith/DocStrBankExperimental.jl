```
findCorr(d::UnivariateDistribution, spec::MSetting)
findCorr(d::dPower, spec::MSetting)
```

M推定における修正項を見つける関数。ψ(Z)の期待値を計算します。ここでZ = (X - μ)/σであり、Xは分布`d`を持ちます。μとσはXの平均と標準偏差です。`d`が指数iのタイプ`dPower`の場合、ψ(Z)の期待値を$Z = (X^i - μ)/σ$で計算します。ここでμとσは$X^i$の期待値と標準偏差です。

# 例

```julia
d = Poisson(10)
spec1 = Huber(1.5)
spec2 = Huber(2)
findCorr(d, spec1)
findCorr(dPower(d, 2), spec2)
```

[`dPower`](@ref dPower)も参照してください。
