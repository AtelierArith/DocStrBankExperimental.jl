```julia
visualize(
    obv::OnlineTechnicalIndicators.OBV,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

1つのlwc_lineを使用して、オンバランスボリューム（OBV）を視覚化します。
