```
function get_ρ(Sₐ::Raster, Θ::Raster, p::Raster)
function get_ρ(stack::RasterStack, var_names::NamedTuple)
function get_ρ(series::RasterStack, var_names::NamedTuple)
```

Compute in-situ density, `ρ`, using `gsw_rho` from GibbsSeaWater.jl. This computation depends on absolute salinity (`Sₐ`), conservative temperature (`Θ`) and pressure (`p`). To compute ρ from a `RasterStack` or `RasterSeries` the variable names must be passed into the function as a `NamedTuple` in the form `(Sₐ = :salt_var, Θ = :temp_var, p = :pressure_var)`. The returned `Raster` will have the same dimensions as `Rasterstack` that is passed in.
