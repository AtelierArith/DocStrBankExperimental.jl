```
RegionGrid(
    geo  :: GeoRegion,
    pnts :: Vector{Point2{FT}};
    rotation  :: Real = 0,
    sigdigits :: Int = 10
) where FT <: Real -> ggrd :: UnstructuredGrid
```

`UnstructuredGrid`型を作成します。このメソッドは、CESM2が立方体スフィア構成で実行されたときの出力のように、構造化されていないグリッドや経度と緯度のポイントのメッシュグリッドにより適しています。

# 引数

  * `geo` : 興味のあるGeoRegion。
  * `pnts` : `Point2(lon,lat)`型の`Vector`。

# キーワード引数

  * `rotation` : GeoRegionの重心を中心に最終的な「逆回転」データをX-Yデカルト座標系（メートル単位）に投影するための回転角（度単位）。`geo.θ`に対して正の値は、重心の周りを反時計回りに最終値を回転させます。デフォルトは0です。

# 戻り値

  * `ggrd` : `UnstructuredGrid`。
