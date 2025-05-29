```julia
initialize!(
    particles::Array{P<:SpeedyWeather.Particle, 1},
    model::SpeedyWeather.AbstractModel
)

```

Initialize particle locations uniformly in latitude, longitude and in the vertical σ coordinates. This uses a cosin-distribution in latitude for an equal-area uniformity.
