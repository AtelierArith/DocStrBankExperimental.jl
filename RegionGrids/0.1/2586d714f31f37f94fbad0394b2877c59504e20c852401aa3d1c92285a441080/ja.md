```
RegionGrid(
    geo  :: GeoRegion,
    pnts :: Array{Point2{FT}};
    rotation  :: Real = 0,
    sigdigits :: Int = 10
) where FT <: Real -> ggrd :: GeneralizedGrid
```

指定された引数に基づいて `GeneralizedGrid` 型を作成します。このメソッドは、WRFの出力のような経度と緯度の点の構造化されていない非直線的（例：曲線的）グリッドにより適しています。

# 引数

  * `geo` : 興味のある GeoRegion。
  * `pnts` : `Point2(lon,lat)` 型の配列。

# キーワード引数

  * `rotation` : GeoRegion セントロイドの周りで最終的な「デローテーション」データを X-Y デカルト座標系（メートル単位）に投影するための回転角度（度単位）。`geo.θ` に対して正の値は、セントロイドの周りを反時計回りに最終値を回転させます。デフォルトは 0。

# 戻り値

  * `ggrd` : `GeneralizedGrid`。
