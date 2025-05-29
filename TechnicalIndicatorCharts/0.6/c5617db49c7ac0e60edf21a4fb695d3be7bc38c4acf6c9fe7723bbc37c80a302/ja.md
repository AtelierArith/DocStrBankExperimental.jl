```julia
visualize(
    obv::OnlineTechnicalIndicators.OBV,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

オンバランスボリューム (OBV) を 1 lwc_line を使用して視覚化します。
