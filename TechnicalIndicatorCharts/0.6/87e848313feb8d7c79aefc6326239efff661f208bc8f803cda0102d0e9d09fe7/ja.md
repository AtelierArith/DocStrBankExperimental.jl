```julia
visualize(
    dema::OnlineTechnicalIndicators.DEMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

1本のlwc_lineを使用してDEMAを視覚化します。
