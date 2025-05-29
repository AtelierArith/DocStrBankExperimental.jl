```julia
initialize!(
    progn_new::SpeedyWeather.PrognosticVariables,
    initial_conditions::SpeedyWeather.StartFromFile,
    model::SpeedyWeather.AbstractModel
)

```

Restart from a previous SpeedyWeather.jl simulation via the restart file restart.jld2 Applies interpolation in the horizontal but not in the vertical.
