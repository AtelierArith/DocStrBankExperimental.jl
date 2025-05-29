```julia
deactivate(
    p::SpeedyWeather.Particle{NF}
) -> SpeedyWeather.Particle{_A, false} where _A<:AbstractFloat

```

Deactivate particle. Inactive particles cannot move.
