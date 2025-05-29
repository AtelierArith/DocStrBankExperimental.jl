```
function get_α(Sₐ::Raster, Θ::Raster, p::Raster)
function get_α(stack::RasterStack, var_names::NamedTuple)
function get_α(series::RasterSeries, var_names::NamedTuple)
```

Compute the thermal exapnsion coefficient, `α`, using `gsw_alpha` from GibbsSeaWater.jl. To compute `α` from a `RasterStack` or `RasterSeries` the variable names must be passed into the function as a `NamedTuple` in the form `(Sₐ = :salt_var, Θ = :temp_var, p = :pressure_var)`. The returned `Raster` will have the same dimensions as `Rasterstack` that is passed in.
