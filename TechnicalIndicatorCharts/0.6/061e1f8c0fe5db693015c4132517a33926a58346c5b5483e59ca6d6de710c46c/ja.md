```julia
update!(
    chart::TechnicalIndicatorCharts.Chart,
    c::TechnicalIndicatorCharts.Candle
) -> Union{Nothing, TechnicalIndicatorCharts.Candle}

```

チャートをキャンドルで更新します。キャンドルが完成した場合、それを返します。そうでない場合、更新時に何も返しません。
