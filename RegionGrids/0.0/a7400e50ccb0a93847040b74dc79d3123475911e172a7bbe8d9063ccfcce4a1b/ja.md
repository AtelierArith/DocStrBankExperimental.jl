```
RegionGrid(
    geo  :: Union{RectRegion,PolyRegion},
    pnts :: Vector{Point2{FT}}
) where FT <: Real -> ggrd :: VectorMask
```

`VectorMask`型を、 

# 引数

  * `geo` : 興味のあるGeoRegion
  * `pnts` : 経度ポイントを含む`Float`型の`Vector`

# 戻り値

  * `ggrd` : `VectorMask`
