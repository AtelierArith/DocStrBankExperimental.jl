```
function get_β(Sₐ::Raster, Θ::Raster, p::Raster)
function get_β(stack::RasterStack, var_names::NamedTuple)
function get_β(series::RasterSeries, var_names::NamedTuple)
```

Compute the haline contraction coefficient, `β`, using `gsw_beta` from GibbsSeaWater.jl. To compute `β` from a `RasterStack` or `RasterSeries` the variable names must be passed into the function as a `NamedTuple` in the form `(Sₐ = :salt_var, Θ = :temp_var, p = :pressure_var)`. The returned `Raster` will have the same dimensions as `Rasterstack` that is passed in.
