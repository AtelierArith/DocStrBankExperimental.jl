```julia
set!(
    model::SpeedyWeather.AbstractModel;
    orography,
    land_sea_mask,
    kwargs...
)

```

Sets a boundary condition fields for `model`. The input can be a function, `RingGrid`, `LowerTriangularMatrix`,  or scalar as for other `set!` functions. If the keyword `add==true` the input is added to the exisiting  field instead.
