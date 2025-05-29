```julia
initialize!(
    output::SpeedyWeather.NetCDFOutput{Grid2D, Grid3D, Interpolator},
    feedback::SpeedyWeather.AbstractFeedback,
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    model::SpeedyWeather.AbstractModel
)

```

Initialize NetCDF `output` by creating a netCDF file and storing the initial conditions of `diagn` (and `progn`). To be called just before the first timesteps.
