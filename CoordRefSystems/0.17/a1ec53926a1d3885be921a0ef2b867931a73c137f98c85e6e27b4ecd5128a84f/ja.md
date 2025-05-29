```
GeodeticLatLon(lat, lon)
GeodeticLatLon{Datum}(lat, lon)
```

測地線緯度 `lat ∈ [-90°,90°]` と経度 `lon ∈ [-180°,180°]` は角度単位（デフォルトは度）で、指定された `Datum`（デフォルトは `WGS84Latest`）を持ちます。

## 例

```julia
GeodeticLatLon(45, 45) # デフォルト単位を追加
GeodeticLatLon(45°, 45°) # 整数は浮動小数点数に変換されます
GeodeticLatLon((π/4)rad, (π/4)rad) # ラジアンは度に変換されます
GeodeticLatLon(45.0°, 45.0°)
GeodeticLatLon{WGS84Latest}(45.0°, 45.0°)
```

[EPSG:4326](https://epsg.io/4326)を参照してください。
