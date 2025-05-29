```
rand(d::dPower)
rand(d::dPower, n::Int64)
rand(d::dPower, dims::Dims)
```

データ型 `dPower` の乱数生成。

# 例

```julia
dX = Poisson(10)
dY = dPower(dX, 2)
rand(dY)
rand(dY, 100)
rand(dY, (100, 100))
```

関連項目 [`dPower`](@ref dPower).
