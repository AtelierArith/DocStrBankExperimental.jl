```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables{NF},
    initial_conditions::SpeedyWeather.RandomWaves,
    model::SpeedyWeather.ShallowWater
)

```

Random initial conditions for the interface displacement η in the shallow water equations. The flow (u, v) is zero initially. This kicks off gravity waves that will interact with orography.
