```julia
visualize(
    srsi::OnlineTechnicalIndicators.StochRSI,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> Vector{LightweightCharts.LWCChart}

```

StochRSIを2つのlwc_linesを使用して視覚化します。
