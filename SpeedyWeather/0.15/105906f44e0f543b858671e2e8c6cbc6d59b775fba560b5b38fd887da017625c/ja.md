```julia
initialize!(
    progn::SpeedyWeather.PrognosticVariables,
    _::SpeedyWeather.PressureOnOrography,
    model::SpeedyWeather.PrimitiveEquation
)

```

オロガフィー上の表面圧を、基準温度の層温度勾配を用いて静水圧方程式を統合することによって初期化します。
