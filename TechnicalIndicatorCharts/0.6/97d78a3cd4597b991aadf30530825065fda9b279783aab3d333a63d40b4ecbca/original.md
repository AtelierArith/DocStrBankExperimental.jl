```julia
visualize(
    keltnerchannels::OnlineTechnicalIndicators.KeltnerChannels,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> Vector{LightweightCharts.LWCChart}

```

Visualize Keltner Channels (KC) using 3 lwc_lines.
