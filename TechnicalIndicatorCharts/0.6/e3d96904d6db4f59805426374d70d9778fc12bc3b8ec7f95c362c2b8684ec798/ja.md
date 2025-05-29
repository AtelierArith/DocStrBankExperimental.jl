```julia
visualize(
    sma::OnlineTechnicalIndicators.SMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

SMAインジケーターを視覚化するためのlwc_lineを返します。
