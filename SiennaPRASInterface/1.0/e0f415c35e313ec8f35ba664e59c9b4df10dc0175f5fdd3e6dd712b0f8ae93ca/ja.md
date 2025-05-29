```
make_generator_outage_draws!(
    sys,
    initial_time::Dates.DateTime=nothing,
    resolution::TIMEPERIOD=nothing,
    steps::Int=nothing,
    horizon::Int=nothing,
) where {TIMEPERIOD <: Dates.TimePeriod}
```

システム内の発電機に利用可能時間系列を追加します。

発電機の停止抽出を行うための主な関数です。
