```julia
activate(
    p::SpeedyWeather.Particle{NF}
) -> SpeedyWeather.Particle{_A, true} where _A<:AbstractFloat

```

粒子をアクティブにします。アクティブな粒子は移動できます。
