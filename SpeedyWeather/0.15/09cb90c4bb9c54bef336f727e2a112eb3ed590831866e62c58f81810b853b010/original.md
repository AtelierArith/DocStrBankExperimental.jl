```julia
transform!(
    diagn::SpeedyWeather.DiagnosticVariables,
    progn::SpeedyWeather.PrognosticVariables,
    lf::Integer,
    model::SpeedyWeather.ShallowWater;
    kwargs...
)

```

Propagate the spectral state of the prognostic variables `progn` to the diagnostic variables in `diagn` for the shallow water model. Updates grid vorticity, grid divergence, grid interface displacement (`pres_grid`) and the velocities u, v.
