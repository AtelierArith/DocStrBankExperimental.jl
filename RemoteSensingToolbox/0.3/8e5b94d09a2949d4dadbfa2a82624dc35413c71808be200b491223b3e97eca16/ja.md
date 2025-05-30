```
nbri(src::AbstractSatellite)
nbri(::Type{AbstractSatellite}, stack::AbstractRasterStack)
nbri(nir::AbstractRaster, swir2::AbstractRaster)
```

正規化焼失比指数を計算します。

NBRIは焼失した領域を強調するために使用されます。

NBRI = (nir - swir2) / (nir + swir2)
