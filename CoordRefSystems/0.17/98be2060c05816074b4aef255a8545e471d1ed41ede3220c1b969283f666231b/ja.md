```
Cartesian3D(x, y, z)
Cartesian3D{Datum}(x, y, z)
Cartesian3D((x, y, z))
Cartesian3D{Datum}((x, y, z))
```

3つの座標を持つ[`Cartesian`](@ref)へのエイリアスです。

## 例

```julia
Cartesian3D(1, 1, 1) # デフォルトの単位を追加
Cartesian3D(1m, 1m, 1m) # 整数は浮動小数点数に変換されます
Cartesian3D(1.0km, 1.0km, 1.0km)
Cartesian3D{WGS84Latest}(1.0m, 1.0m, 1.0m)
```
