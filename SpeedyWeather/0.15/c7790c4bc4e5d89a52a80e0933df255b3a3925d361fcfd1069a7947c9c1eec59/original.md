```julia
initialize!(
    clock::SpeedyWeather.Clock,
    time_stepping::SpeedyWeather.AbstractTimeStepper,
    args...
) -> Any

```

Initialize the clock with the time step `Δt` from `time_stepping`.
