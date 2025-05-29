```julia
get_edges_avg_props(
    model::Union{EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.StaticType}},
    props::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
