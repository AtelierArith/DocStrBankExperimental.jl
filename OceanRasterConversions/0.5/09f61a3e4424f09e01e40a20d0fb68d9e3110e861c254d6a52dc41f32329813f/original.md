```
function Sₚ_to_Sₐ(Sₚ::Raster)
function Sₚ_to_Sₐ(stack::RasterStack, Sₚ::Symbol)
function Sₚ_to_Sₐ(series::RasterSeries, Sₚ::Symbol)
```

Convert a `Raster` of practical salinity (`Sₚ`) to absolute salinity (`Sₐ`) using `gsw_sa_from_sp` from GibbsSeaWater.jl. This conversion depends on pressure. If converting from a `RasterStack` or `RasterSeries`, the symbol for the practical salinity in the `RasterStack/Series` must be passed in as a `Symbol` –-  that is if the variable name is SALT the `RasterStack/Series`, the `Symbol` `:SALT` must be passed in.
