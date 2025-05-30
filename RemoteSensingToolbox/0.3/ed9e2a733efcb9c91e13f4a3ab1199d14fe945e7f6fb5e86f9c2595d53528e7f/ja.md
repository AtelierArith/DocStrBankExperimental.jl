```
mndwi(src::AbstractSatellite)
mndwi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
mndwi(green::AbstractRaster, swir::AbstractRaster)
```

修正正規化差水指数を計算します (Xu 2006)。

MNDWI = (green - swir) / (green + swir)
