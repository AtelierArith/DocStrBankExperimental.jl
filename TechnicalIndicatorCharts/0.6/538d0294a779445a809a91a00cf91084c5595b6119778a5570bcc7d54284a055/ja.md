```julia
visualize(
    hma::OnlineTechnicalIndicators.HMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

HMAを1つのlwc_lineを使用して視覚化します。
