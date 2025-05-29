```julia
visualize(
    SMMA::OnlineTechnicalIndicators.SMMA,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> LightweightCharts.LWCChart

```

Return an lwc_line for visualizing an SMMA indicator.
