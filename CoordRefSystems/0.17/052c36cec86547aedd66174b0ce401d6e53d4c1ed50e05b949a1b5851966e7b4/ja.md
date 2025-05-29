```
LatLonAlt(lat, lon, alt)
LatLonAlt{Datum}(lat, lon, alt)
```

[`GeodeticLatLonAlt`](@ref)へのエイリアスです。

## 例

```julia
LatLonAlt(45, 45, 1) # デフォルト単位を追加
LatLonAlt(45°, 45°, 1m) # 整数は浮動小数点数に変換されます
LatLonAlt((π/4)rad, (π/4)rad) # ラジアンは度に変換されます
LatLonAlt(45.0°, 45.0°, 1.0km) # 長さの量はメートルに変換されます
LatLonAlt(45.0°, 45.0°, 1.0m)
LatLonAlt{WGS84Latest}(45.0°, 45.0°, 1.0m)
```
