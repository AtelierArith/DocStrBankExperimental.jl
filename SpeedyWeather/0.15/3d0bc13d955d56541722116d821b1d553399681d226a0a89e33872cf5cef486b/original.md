```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    model::SpeedyWeather.PrimitiveEquation;
    initialize
)

```

Propagate the spectral state of the prognostic variables `progn` to the diagnostic variables in `diagn` for primitive equation models. Updates grid vorticity, grid divergence, grid temperature, pressure (`pres_grid`) and the velocities u, v.
