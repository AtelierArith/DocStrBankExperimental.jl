```
AuthalicLatLon(lat, lon)
AuthalicLatLon{Datum}(lat, lon)
```

Authalic 緯度 `lat ∈ [-90°,90°]` と経度 `lon ∈ [-180°,180°]` は角度単位（デフォルトは度）で、指定された `Datum`（デフォルトは `WGS84`）を持ちます。

## 例

```julia
AuthalicLatLon(45, 45) # デフォルト単位を追加
AuthalicLatLon(45°, 45°) # 整数は浮動小数点数に変換されます
AuthalicLatLon((π/4)rad, (π/4)rad) # ラジアンは度に変換されます
AuthalicLatLon(45.0°, 45.0°)
AuthalicLatLon{WGS84Latest}(45.0°, 45.0°)
```
