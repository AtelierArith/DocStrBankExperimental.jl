```
skewness(d::dPower)
```

`dPower` 確率変数の歪度。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
skewness(dPower)
```

関連項目 [`dPower`](@ref dPower)。
