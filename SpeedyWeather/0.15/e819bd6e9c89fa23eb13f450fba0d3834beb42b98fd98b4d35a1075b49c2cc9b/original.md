```julia
initialize!(
    clock::SpeedyWeather.Clock,
    Δt::Dates.Period,
    period::Dates.Period
) -> SpeedyWeather.Clock

```

Initialize the clock with the time step `Δt` and `period` to integrate for.
