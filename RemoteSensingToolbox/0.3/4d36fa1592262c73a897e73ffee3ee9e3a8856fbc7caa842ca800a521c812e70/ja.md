```
ndwi(src::AbstractSatellite)
ndwi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndwi(green::AbstractRaster, nir::AbstractRaster)
```

正規化差水指数を計算します (McFeeters 1996)。

NDWI = (green - nir) / (green + nir)
