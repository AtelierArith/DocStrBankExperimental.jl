```julia
initialize!(
    clock::SpeedyWeather.Clock,
    Δt::Dates.Period,
    period::Dates.Period
) -> SpeedyWeather.Clock

```

`Δt` と `period` を統合するために、時計を初期化します。
