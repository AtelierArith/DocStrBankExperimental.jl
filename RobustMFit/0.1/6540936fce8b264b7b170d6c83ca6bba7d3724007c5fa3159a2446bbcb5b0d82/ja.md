```
cdf(d::dPower, x::Real)
```

`dPower`分布の累積分布関数。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
cdf(dPower, 2)
```

[`dPower`](@ref dPower)も参照してください。
