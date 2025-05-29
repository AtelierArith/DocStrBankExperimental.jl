```julia
initialize!(
    scheme::SpeedyWeather.HeldSuarez,
    model::SpeedyWeather.PrimitiveEquation
)

```

HeldSuarezの温度緩和を初期化し、平衡温度Teqのための項を事前計算します。
