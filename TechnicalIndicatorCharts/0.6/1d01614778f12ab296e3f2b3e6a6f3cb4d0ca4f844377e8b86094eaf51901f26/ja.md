```julia
visualize(
    ema::OnlineTechnicalIndicators.EMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

1つのlwc_lineを使用してEMAを視覚化します。
