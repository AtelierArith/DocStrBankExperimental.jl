```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables,
    initial_conditions::SpeedyWeather.RossbyHaurwitzWave,
    model::SpeedyWeather.AbstractModel
)

```

Rossby-Haurwitz wave initial conditions as in Williamson et al. 1992, J Computational Physics with an additional cut-off amplitude `c` to filter out tiny harmonics in the vorticity field.
