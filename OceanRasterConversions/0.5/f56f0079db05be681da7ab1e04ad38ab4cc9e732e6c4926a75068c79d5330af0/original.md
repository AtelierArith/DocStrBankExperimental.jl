```
function θ_to_Θ(θ::Raster, Sₐ::Raster)
function θ_to_Θ(stack::RasterStack, var_names::NamedTuple)
function θ_to_Θ(series::RasterSeries, var_names::NamedTuple)
```

Convert a `Raster` of potential temperature (`θ`) to conservative temperature (`Θ`) using `gsw_ct_from_pt`  from GibbsSeaWater.jl. This conversion depends on absolute salinity. If converting from a  from a `RasterStack` or a `RasterSeries`, the `var_names` must be passed in as for `convert_ocean_vars` –-  that is, as a named tuple in the form `(Sₚ = :salt_name, θ = :potential_temp_name)` where `:potential_temp_name` and `:salt_name` are the name of the potential temperature and salinity in the `RasterStack`.
