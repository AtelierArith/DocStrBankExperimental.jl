```julia
initialize!(
    clock::SpeedyWeather.Clock,
    Δt::Dates.Period,
    n_timesteps::Integer
) -> SpeedyWeather.Clock

```

Initialize the clock with the time step `Δt` and the number of time steps `n_timesteps`.
