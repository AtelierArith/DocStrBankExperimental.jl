```
Cartesian2D(x, y)
Cartesian2D{Datum}(x, y)
Cartesian2D((x, y))
Cartesian2D{Datum}((x, y))
```

2つの座標を持つ[`Cartesian`](@ref)へのエイリアスです。

## 例

```julia
Cartesian2D(1, 1) # デフォルトの単位を追加
Cartesian2D(1m, 1m) # 整数は浮動小数点数に変換されます
Cartesian2D(1.0km, 1.0km)
Cartesian2D{WGS84Latest}(1.0m, 1.0m)
```
