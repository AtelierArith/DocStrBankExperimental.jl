```
kurtosis(d::dPower)
```

`dPower` 確率変数の尖度。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
kurtosis(dPower)
```

関連項目 [`dPower`](@ref dPower).
