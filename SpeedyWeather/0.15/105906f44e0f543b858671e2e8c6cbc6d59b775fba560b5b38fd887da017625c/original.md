```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables,
    _::SpeedyWeather.PressureOnOrography,
    model::SpeedyWeather.PrimitiveEquation
)

```

Initialize surface pressure on orography by integrating the hydrostatic equation with the reference temperature lapse rate.
