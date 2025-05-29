```
LatLon(lat, lon)
LatLon{Datum}(lat, lon)
```

[`GeodeticLatLon`](@ref)へのエイリアスです。

## 例

```julia
LatLon(45, 45) # デフォルトの単位を追加
LatLon(45°, 45°) # 整数は浮動小数点数に変換されます
LatLon((π/4)rad, (π/4)rad) # ラジアンは度に変換されます
LatLon(45.0°, 45.0°)
LatLon{WGS84Latest}(45.0°, 45.0°)
```

[EPSG:4326](https://epsg.io/4326)を参照してください。
