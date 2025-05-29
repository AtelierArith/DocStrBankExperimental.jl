```julia
initialize!(
    callback::SpeedyWeather.GlobalSurfaceTemperatureCallback{NF},
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    model::SpeedyWeather.AbstractModel
) -> Int64

```

Initializes callback.temp vector that records the global mean surface temperature on every time step. Allocates vector of correct length (number of elements = total time steps plus one) and stores the global surface temperature of the initial conditions
