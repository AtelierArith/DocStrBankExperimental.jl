```julia
visualize(
    sma::OnlineTechnicalIndicators.SMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

Return an lwc_line for visualizing an SMA indicator.
