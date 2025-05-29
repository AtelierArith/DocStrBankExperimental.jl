```julia
set!(
    L::SpeedyWeather.AbstractTimeStepper,
    Δt::Dates.Period
) -> SpeedyWeather.AbstractTimeStepper

```

タイムステッパー `L` の時間ステップを `Δt`（スケールなし）に変更し、出力周波数の調整を無効にします。
