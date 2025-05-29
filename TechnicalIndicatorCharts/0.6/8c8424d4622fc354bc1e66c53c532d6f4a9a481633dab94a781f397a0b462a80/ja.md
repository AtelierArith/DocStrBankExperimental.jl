```julia
visualize(
    rsi::OnlineTechnicalIndicators.RSI,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

1つのlwc_lineを使用してRSIを視覚化します。
