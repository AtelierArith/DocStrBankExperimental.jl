```julia
move(
    p::SpeedyWeather.Particle{NF, true},
    dlon,
    dlat
) -> SpeedyWeather.Particle{_A, true} where _A<:AbstractFloat

```

2Dでの増分(dlon, dlat)を使って粒子を移動させます。垂直σ方向には移動しません。アクティブな粒子のみが移動します。
