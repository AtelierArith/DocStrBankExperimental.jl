```
ndmi(src::AbstractSatellite)
ndmi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
ndmi(nir::AbstractRaster, swir1::AbstractRaster)
```

Compute the Normalized Difference Moisture Index.

NDMI is sensitive to the moisture levels in vegetation. It is used to monitor droughts and fuel levels in fire-prone areas.

NDMI = (nir - swir1) / (nir + swir1)
