```
ndwi(src::AbstractSatellite)
ndwi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndwi(green::AbstractRaster, nir::AbstractRaster)
```

Compute the Normalized Difference Water Index (McFeeters 1996).

NDWI = (green - nir) / (green + nir)
