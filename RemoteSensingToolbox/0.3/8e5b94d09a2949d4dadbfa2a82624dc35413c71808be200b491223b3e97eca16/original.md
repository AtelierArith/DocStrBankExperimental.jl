```
nbri(src::AbstractSatellite)
nbri(::Type{AbstractSatellite}, stack::AbstractRasterStack)
nbri(nir::AbstractRaster, swir2::AbstractRaster)
```

Compute the Normalized Burn Ratio Index.

NBRI is used to emphasize burned areas.

NBRI = (nir - swir2) / (nir + swir2)
