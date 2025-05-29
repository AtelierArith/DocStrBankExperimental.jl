```
insupport(d::dPower, x::Real)
```

分布 `d` のサポートに `x` が含まれているかを確認します。ここで、`d` は `dPower` 型です。

# 例

```julia
dX = Poisson(10)
dY = dPower(dX, 2)
insupport(dPower, 9)
```

関連情報は [`dPower`](@ref dPower) を参照してください。
