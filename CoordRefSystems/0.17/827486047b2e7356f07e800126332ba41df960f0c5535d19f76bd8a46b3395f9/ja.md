```
GeocentricLatLonAlt(lat, lon, alt)
GeocentricLatLonAlt{Datum}(lat, lon, alt)
```

地心緯度 `lat ∈ [-90°,90°]` および経度 `lon ∈ [-180°,180°]` は角度単位（デフォルトは度）で、標高は長さ単位（デフォルトはメートル）で、指定された `Datum`（デフォルトは `WGS84Latest`）を持ちます。
