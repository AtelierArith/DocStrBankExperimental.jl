```
IF(d::UnivariateDistribution, spec::MSetting)
IF(d::dPower, spec::MSetting)
```

分布 `d` と仕様 `spec` に基づく影響関数。関数 z -> -ψ(z)/E(ψder(Z)) として定義され、ここで Z = (X - μ)/σ および z = (x - μ)/σ です。

# 例

```julia
d = Poisson(10)
spec = Huber(1.5)
IFpois = IF(d, spec)
IFpois(1)
```

関連情報 MSetting: [`Huber`](@ref Huber), [`Tukey`](@ref Tukey), [`Andrew`](@ref Andrew) および [`Hampel`](@ref Hampel).
