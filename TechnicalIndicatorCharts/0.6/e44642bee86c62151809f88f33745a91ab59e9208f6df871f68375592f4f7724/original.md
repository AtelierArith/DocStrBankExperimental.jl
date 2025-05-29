```julia
visualize(
    tsi::OnlineTechnicalIndicators.TSI,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

Visualize True Strength Index (TSI) using 1 lwc_line. Note that on TradingView, TSI includes a second signal line that is not included here.
