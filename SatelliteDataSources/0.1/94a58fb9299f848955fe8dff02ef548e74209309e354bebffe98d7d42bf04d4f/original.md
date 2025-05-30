```
RasterStack(x::AbstractSatellite, layers=bands(T); kwargs...)
```

Read multiple layers into a `Rasters.RasterStack`.

# Parameters

  * `x`: An `AbstractSatellite` from which to read a layer.
  * `layer`: The layer to be read. See `layers(s)` for a list of available layers for sensor `s`.
  * `kwargs`: Refer to the `Rasters.RasterStack` [documentation](https://rafaqz.github.io/Rasters.jl/dev/reference/#Rasters.RasterStack) for a summary of supported keywords.
