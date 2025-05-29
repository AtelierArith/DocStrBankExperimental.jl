```julia
initialize!(
    scheme::SpeedyWeather.JablonowskiRelaxation,
    model::SpeedyWeather.PrimitiveEquation
)

```

JablonowskiRelaxationの温度緩和を、平衡温度Teqと緩和の強さ（周波数）の項を事前計算することで初期化します。
