```julia
get_nums_nodes(
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}},
    conditions::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
