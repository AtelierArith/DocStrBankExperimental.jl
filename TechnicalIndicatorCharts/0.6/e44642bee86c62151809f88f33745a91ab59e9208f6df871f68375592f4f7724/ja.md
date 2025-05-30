```julia
visualize(
    tsi::OnlineTechnicalIndicators.TSI,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

真の強さ指数 (TSI) を 1 lwc_line を使用して視覚化します。TradingView では、TSI にここに含まれていない2番目のシグナルラインが含まれていることに注意してください。
