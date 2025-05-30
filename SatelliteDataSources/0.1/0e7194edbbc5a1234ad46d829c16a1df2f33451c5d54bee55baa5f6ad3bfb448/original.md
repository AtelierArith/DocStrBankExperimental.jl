```
Raster(x::AbstractSatellite, layer::Symbol; kwargs...)
```

Read a single layer into a `Rasters.Raster`.

# Parameters

  * `x`: An `AbstractSatellite` from which to read a layer.
  * `layer`: The layer to be read. See `layers(s)` for a list of available layers for sensor `s`.
  * `kwargs`: Refer to the `Rasters.Raster` [documentation](https://rafaqz.github.io/Rasters.jl/dev/reference/#Rasters.Raster) for a summary of supported keywords.
