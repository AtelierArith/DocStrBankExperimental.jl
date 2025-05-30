```
ndbi(src::AbstractSatellite)
ndbi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndbi(swir1::AbstractRaster, nir::AbstractRaster)
```

正規化差分構築指数を計算します

NDBIは都市および構築された地域を強調するために使用されます。

NDBI = (swir1 - nir) / (swir1 + nir)
