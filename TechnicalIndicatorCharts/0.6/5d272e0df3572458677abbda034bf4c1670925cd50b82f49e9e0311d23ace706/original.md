```julia
visualize(
    bb::OnlineTechnicalIndicators.BB,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> Vector{LightweightCharts.LWCChart}

```

Visualize Bollinger Bands using 3 lwc_lines.
