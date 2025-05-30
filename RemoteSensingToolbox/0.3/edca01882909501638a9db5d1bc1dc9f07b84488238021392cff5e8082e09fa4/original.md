```
ndbi(src::AbstractSatellite)
ndbi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndbi(swir1::AbstractRaster, nir::AbstractRaster)
```

Compute the The Normalized Difference Built-up Index

NDBI is used to emphasize urban and built-up areas.

NDBI = (swir1 - nir) / (swir1 + nir)
