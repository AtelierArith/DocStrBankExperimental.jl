```julia
visualize(
    srsi::OnlineTechnicalIndicators.StochRSI,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> Vector{LightweightCharts.LWCChart}

```

Visualize StochRSI using 2 lwc_lines.
