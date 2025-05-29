```julia
move(
    p::SpeedyWeather.Particle{NF, true},
    dlon,
    dlat,
    dσ
) -> SpeedyWeather.Particle{_A, true} where _A<:AbstractFloat

```

Move a particle with increments (dlon, dlat, dσ) in those respective coordinates. Only active particles are moved.
