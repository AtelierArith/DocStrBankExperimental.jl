```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    model::SpeedyWeather.Barotropic;
    kwargs...
)

```

Propagate the spectral state of the prognostic variables `progn` to the diagnostic variables in `diagn` for the barotropic vorticity model. Updates grid vorticity, spectral stream function and spectral and grid velocities u, v.
