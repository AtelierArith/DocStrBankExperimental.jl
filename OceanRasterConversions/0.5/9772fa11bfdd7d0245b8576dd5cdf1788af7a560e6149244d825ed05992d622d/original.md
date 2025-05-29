```
function get_σₚ(Sₐ::Raster, Θ::Raster, p::Number)
function get_σₚ(stack::RasterStack, var_names::NamedTuple)
function get_σₚ(series::RasterStack, var_names::NamedTuple)
```

Compute potential density at reference pressure `p`, `σₚ`, using `gsw_rho` from GibbsSeaWater.jl. This computation depends on absolute salinity (`Sₐ`), conservative temperature (`Θ`) and a user entered reference pressure (`p`). Compute and return the potential density `σₚ` at reference pressure `p` from a `RasterStack` or `RasterSeries`. This computation depends on absolute salinity `Sₐ`, conservative temperature `Θ` and a reference pressure `p`. The variable names must be passed into the function as a `NamedTuple` in the form `(Sₐ = :salt_var, Θ = :temp_var, p = ref_pressure)`. Note `p` in this case is a number. The returned `Raster` will have the same dimensions as `Rasterstack` that is passed in.
