```julia
initialize!(
    clock::SpeedyWeather.Clock,
    time_stepping::SpeedyWeather.AbstractTimeStepper,
    args...
) -> Any

```

`time_stepping`からの時間ステップ`Δt`で時計を初期化します。
