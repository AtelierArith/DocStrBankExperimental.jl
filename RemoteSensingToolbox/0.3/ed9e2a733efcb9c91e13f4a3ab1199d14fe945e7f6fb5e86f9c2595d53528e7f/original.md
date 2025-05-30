```
mndwi(src::AbstractSatellite)
mndwi(::Type{AbstractSatellite}, stack::AbstractRasterStack)
mndwi(green::AbstractRaster, swir::AbstractRaster)
```

Compute the Modified Normalised Difference Water Index (Xu 2006).

MNDWI = (green - swir) / (green + swir)
