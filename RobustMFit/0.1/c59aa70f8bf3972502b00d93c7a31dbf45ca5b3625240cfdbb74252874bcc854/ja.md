```
mean(d::dPower)
```

`dPower` 確率変数の平均/期待値。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
mean(dPower)
```

関連項目 [`dPower`](@ref dPower)。
