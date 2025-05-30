```
ndvi(src::AbstractSatellite)
ndvi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndvi(nir::AbstractRaster, red::AbstractRaster)
```

正規化差分植生指数を計算します。

NDVI = (nir - red) / (nir + red)
