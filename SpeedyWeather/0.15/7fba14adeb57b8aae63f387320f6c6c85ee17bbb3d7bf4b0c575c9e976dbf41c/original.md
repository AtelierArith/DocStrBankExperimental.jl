```julia
isscheduled(
    S::SpeedyWeather.Schedule,
    clock::SpeedyWeather.Clock
) -> Bool

```

Evaluate whether (e.g. a callback) should be scheduled at the timestep given in clock. Returns true for scheduled executions, false for no execution on this time step.
