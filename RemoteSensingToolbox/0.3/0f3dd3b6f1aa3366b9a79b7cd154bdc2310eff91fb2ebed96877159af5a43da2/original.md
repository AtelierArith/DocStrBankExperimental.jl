```
ndvi(src::AbstractSatellite)
ndvi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndvi(nir::AbstractRaster, red::AbstractRaster)
```

Compute the Normalized Difference Vegetation Index.

NDVI = (nir - red) / (nir + red)
