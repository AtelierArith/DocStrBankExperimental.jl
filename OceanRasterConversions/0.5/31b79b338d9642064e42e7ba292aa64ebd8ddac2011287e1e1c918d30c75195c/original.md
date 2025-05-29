```
function convert_ocean_vars(raster::RasterStack, var_names::NamedTuple;
                            ref_pressure = nothing,
                            with_α = false,
                            with_β = false)
function convert_ocean_vars(raster::Rasterseries, var_names::NamedTuple;
                            ref_pressure = nothing,
                            with_α = false,
                            with_β = false)
```

Convert ocean variables depth, practical salinity and potential temperature to pressure, absolute salinity and conservative temperature. All conversions are done using the julia implementation of TEOS-10 [GibbsSeaWater.jl](https://github.com/TEOS-10/GibbsSeaWater.jl). A new `Raster` is returned that contains the variables pressure, absolute salinity, conservative temperature and density (either in-situ or referenced to a user defined reference pressure). As pressure depends on latitude and depth, it is added as a new variable –- that is, each longitude, latitude, depth and time have a variable for pressure. A density variable is also computed which, by default, is *in-situ* density. Potential density at a reference pressure can be computed instead by passing a the keyword argument `ref_pressure`. Optional keyword arguments `with_α` and `with_β` allow the thermal expansion and haline contraction coefficients (respectively) to be computed and added to the returned `RasterStack/Series`.

The name of the variables for potential temperature and practical salinity must be passed in as a `NamedTuple` of the form `(Sₚ = :salt_name, θ = :potential_temp_name)` where `:potential_temp_name` and `:salt_name` are the name of the potential temperature and practical salinity in the `Raster`.
