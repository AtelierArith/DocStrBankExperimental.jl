```
encode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRaster; encoding_type=UInt16, missingval=0x0000)
encode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRasterStack; kwargs...)
```

Encode the provided raster(s) to Digital Numbers (DN).

# Parameters

  * `s`: The `AbstractSatellite` that produced the raster(s) in question.
  * `raster`: Either a `Rasters.Raster` or `Rasters.RasterStack` to be encoded.
  * `encoding_type`: The Julia type to use for storing the encoded values (default = `UInt16`).
  * `missingval`: The value to denote missing values (default = `0x0000`).
