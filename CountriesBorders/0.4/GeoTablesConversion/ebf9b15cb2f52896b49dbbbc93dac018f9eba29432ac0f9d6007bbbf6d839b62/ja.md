```
CountryBorder{T} <: Geometry{🌐,LATLON{T}}
```

国の境界の座標を表す構造体（NaturalEarthデータベースに基づく）。 `T` は境界座標の浮動小数点精度で、デフォルトはFloat32です。

この構造体は、LatLon座標の平坦化近似との比較を高速化するために、LatLonとCartesian2Dの両方で境界を保持します。

# フィールド

  * `admin::String`: 国の名前、すなわちGeoTableのADMINエントリ。
  * `table_idx::Int`: 元のGeoTableにおける国のインデックス。
  * `valid_polyareas::BitVector`: 元の国のMultiPolygonでスキップされたPolyAreasのインデックス。
  * `resolution::Int`: NaturalEarthデータセットからの基礎的な境界サンプリングの解像度。
  * `latlon::MULTI_LATLON{T}`: LatLon CRSでの境界。
  * `cart::MULTI_LATLON{T}`: Cartesian2D CRSでの境界。
