```julia
visualize(
    SMMA::OnlineTechnicalIndicators.SMMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

SMMAインジケーターを視覚化するためのlwc_lineを返します。
