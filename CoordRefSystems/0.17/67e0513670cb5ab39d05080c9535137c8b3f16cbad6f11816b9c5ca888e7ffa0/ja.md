```
GeodeticLatLonAlt(lat, lon, alt)
GeodeticLatLonAlt{Datum}(lat, lon, alt)
```

測地線緯度 `lat ∈ [-90°,90°]` と経度 `lon ∈ [-180°,180°]` は角度単位（デフォルトは度）で、標高は長さ単位（デフォルトはメートル）で、指定された `Datum`（デフォルトは `WGS84Latest`）を持ちます。

## 例

```julia
GeodeticLatLonAlt(45, 45, 1) # デフォルト単位を追加
GeodeticLatLonAlt(45°, 45°, 1m) # 整数は浮動小数点数に変換されます
GeodeticLatLonAlt((π/4)rad, (π/4)rad) # ラジアンは度に変換されます
GeodeticLatLonAlt(45.0°, 45.0°, 1.0km) # 長さの量はメートルに変換されます
GeodeticLatLonAlt(45.0°, 45.0°, 1.0m)
GeodeticLatLonAlt{WGS84Latest}(45.0°, 45.0°, 1.0m)
```
