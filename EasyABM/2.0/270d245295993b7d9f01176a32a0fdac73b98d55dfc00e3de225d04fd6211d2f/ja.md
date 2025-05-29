```julia
get_nodes_avg_props(
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}},
    props::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
