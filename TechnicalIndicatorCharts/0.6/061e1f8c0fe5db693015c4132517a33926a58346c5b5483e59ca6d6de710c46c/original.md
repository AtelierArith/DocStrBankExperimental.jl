```julia
update!(
    chart::TechnicalIndicatorCharts.Chart,
    c::TechnicalIndicatorCharts.Candle
) -> Union{Nothing, TechnicalIndicatorCharts.Candle}

```

Update a chart with a candle. When a candle is completed, return it. Otherwise, return nothing on update.
