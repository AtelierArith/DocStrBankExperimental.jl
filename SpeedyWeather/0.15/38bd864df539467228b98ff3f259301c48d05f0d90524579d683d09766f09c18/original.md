```julia
activate(
    p::SpeedyWeather.Particle{NF}
) -> SpeedyWeather.Particle{_A, true} where _A<:AbstractFloat

```

Activate particle. Active particles can move.
