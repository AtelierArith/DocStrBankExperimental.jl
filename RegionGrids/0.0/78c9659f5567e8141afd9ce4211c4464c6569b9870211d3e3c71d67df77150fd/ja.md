```
RegionGrid(
    geo  :: Union{RectRegion,PolyRegion},
    pnts :: Array{Point2{FT}}
) where FT <: Real -> ggrd :: GeneralMask
```

指定された引数に基づいて `GeneralMask` 型を作成します。このメソッドは、WRFの出力のような経度と緯度の点の構造化されていない非直交（例：曲線的）グリッドにより適しています。

# 引数

  * `geo` : 興味のあるGeoRegion
  * `pnts` : 経度/緯度点を含む `Point2` 型の配列

# 戻り値

  * `ggrd` : `GeneralMask`
