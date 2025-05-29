```julia
initialize!(
    particles::Array{P<:SpeedyWeather.Particle, 1},
    model::SpeedyWeather.AbstractModel
)

```

緯度、経度、および垂直σ座標で粒子の位置を均等に初期化します。これは、等面積の均一性のために緯度でコサイン分布を使用します。
