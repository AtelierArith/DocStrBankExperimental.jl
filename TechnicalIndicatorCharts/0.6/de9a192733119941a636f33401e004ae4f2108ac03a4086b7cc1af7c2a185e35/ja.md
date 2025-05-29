```julia
visualize(
    wma::OnlineTechnicalIndicators.WMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

WMAを1つのlwc_lineを使用して視覚化します。
