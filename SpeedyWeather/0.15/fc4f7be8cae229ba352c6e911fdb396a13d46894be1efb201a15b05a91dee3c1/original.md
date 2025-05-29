```julia
move(
    p::SpeedyWeather.Particle{NF, true},
    dlon,
    dlat
) -> SpeedyWeather.Particle{_A, true} where _A<:AbstractFloat

```

Move a particle with increments (dlon, dlat) in 2D. No movement in vertical σ. Only active particles are moved.
