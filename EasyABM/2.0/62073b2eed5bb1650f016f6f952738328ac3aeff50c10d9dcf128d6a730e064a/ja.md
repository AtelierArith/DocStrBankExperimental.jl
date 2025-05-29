```julia
get_nums_nodes(
    model::Union{EasyABM.GraphModel{EasyABM.StaticType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.StaticType, EasyABM.StaticType}},
    conditions::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
