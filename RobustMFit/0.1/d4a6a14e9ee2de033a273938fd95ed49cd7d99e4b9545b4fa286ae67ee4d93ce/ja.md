```
pdf(d::dPower, x::Real)
```

`dPower`分布の確率（密度）関数。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
pdf(dPower, 2)
```

[`dPower`](@ref dPower)も参照してください。
