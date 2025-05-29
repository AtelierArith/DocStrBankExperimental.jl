```julia
initialize!(
    clock::SpeedyWeather.Clock,
    Δt::Dates.Period,
    n_timesteps::Integer
) -> SpeedyWeather.Clock

```

時間ステップ `Δt` と時間ステップの数 `n_timesteps` で時計を初期化します。
