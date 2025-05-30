```julia
visualize(
    dema::OnlineTechnicalIndicators.DEMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

DEMAを1つのlwc_lineを使用して視覚化します。
