```
ndmi(src::AbstractSatellite)
ndmi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndmi(nir::AbstractRaster, swir1::AbstractRaster)
```

正規化差分水分指数を計算します。

NDMIは植生の水分レベルに敏感です。干ばつや火災の危険がある地域の燃料レベルを監視するために使用されます。

NDMI = (nir - swir1) / (nir + swir1)
