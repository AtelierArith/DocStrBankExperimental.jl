```julia
move(
    p::SpeedyWeather.Particle{NF, true},
    dlon,
    dlat,
    dσ
) -> SpeedyWeather.Particle{_A, true} where _A<:AbstractFloat

```

粒子をそれぞれの座標での増分 (dlon, dlat, dσ) で移動させます。アクティブな粒子のみが移動します。
