```
decode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRaster)
decode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRasterStack)
```

Decode the Digital Number (DN) values in the given raster(s). Typically, the decoded values will be in either reflectance (visual bands) or Kelvin (thermal bands).

# Parameters

  * `s`: The `AbstractSatellite` that produced the raster(s) in question.
  * `raster`: Either a `Rasters.Raster` or `Rasters.RasterStack` to be decoded.
