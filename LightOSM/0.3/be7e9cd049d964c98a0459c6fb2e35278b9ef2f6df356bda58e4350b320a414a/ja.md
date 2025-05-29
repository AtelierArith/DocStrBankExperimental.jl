地理空間座標の表現。

# フィールド

  * `lat::Float64`: 緯度。
  * `lon::Float64`: 経度。
  * `alt::Float64`: 高度。

# コンストラクタ

```
GeoLocation(lat, lon)
GeoLocation(point::Vector{<:Real})
GeoLocation(point_vector::Vector{<:Vector{<:Real}})
GeoLocation(g::OSMGraph, ep::EdgePoint)
```
