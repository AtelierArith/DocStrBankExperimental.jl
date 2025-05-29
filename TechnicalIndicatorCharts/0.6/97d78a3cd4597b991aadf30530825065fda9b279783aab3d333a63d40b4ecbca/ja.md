```julia
visualize(
    keltnerchannels::OnlineTechnicalIndicators.KeltnerChannels,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> Vector{LightweightCharts.LWCChart}

```

Keltner Channels (KC)を3つのlwc_linesを使用して視覚化します。
