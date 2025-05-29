```
quantile(d::dPower, q::Real)
```

`q`-分位数の `dPower` 確率変数。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
quantile(dPower, 0.95)
```

関連項目 [`dPower`](@ref dPower)。
