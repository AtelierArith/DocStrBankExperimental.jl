```julia
deactivate(
    p::SpeedyWeather.Particle{NF}
) -> SpeedyWeather.Particle{_A, false} where _A<:AbstractFloat

```

粒子を非活性化します。非活性化された粒子は移動できません。
