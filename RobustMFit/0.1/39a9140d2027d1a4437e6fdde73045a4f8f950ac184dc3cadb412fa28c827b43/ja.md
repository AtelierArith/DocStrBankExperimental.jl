```
logpdf(d::dPower, x::Real)
```

`dPower`分布の確率（密度）関数の対数。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
logpdf(dPower, 2)
```

[`dPower`](@ref dPower)も参照してください。
