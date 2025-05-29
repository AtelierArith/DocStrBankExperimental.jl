```
var(d::dPower)
```

`dPower` 確率変数の分散。

# 例

```julia
dX = Normal()
dY = dPower(dX, 2)
var(dPower)
```

関連項目として [`dPower`](@ref dPower) を参照してください。
