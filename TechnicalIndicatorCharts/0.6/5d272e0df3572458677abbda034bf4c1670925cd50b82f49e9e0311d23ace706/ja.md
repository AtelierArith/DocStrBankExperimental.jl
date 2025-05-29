```julia
visualize(
    bb::OnlineTechnicalIndicators.BB,
    opts::Union{Nothing, AbstractDict},
    df::DataFrames.DataFrame
) -> Vector{LightweightCharts.LWCChart}

```

3つのlwc_linesを使用してボリンジャーバンドを視覚化します。
