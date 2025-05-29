```
RegionGrid(
    geo  :: TiltRegion,
    pnts :: Array{Point2{FT}}
) where FT <: Real -> ggrd :: GeneralTilt
```

指定された引数に基づいて `GeneralTilt` 型を作成します。このメソッドは、WRFの出力のような経度と緯度の点の構造化された非直交（例：曲線）グリッドにより適しています。

# 引数

  * `geo` : 興味のあるGeoRegion
  * `pnts` : 経度/緯度点を含む `Point2` 型の配列

# 戻り値

  * `ggrd` : `GeneralTilt`
