```julia
get_nodes_avg_props(
    model::Union{EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.StaticType}},
    props::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
