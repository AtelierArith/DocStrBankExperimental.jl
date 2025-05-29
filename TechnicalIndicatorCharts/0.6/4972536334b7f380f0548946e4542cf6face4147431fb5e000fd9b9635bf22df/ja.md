```julia
visualize(
    atr::OnlineTechnicalIndicators.ATR,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

ATRを1つのlwc_lineを使用して視覚化します。
