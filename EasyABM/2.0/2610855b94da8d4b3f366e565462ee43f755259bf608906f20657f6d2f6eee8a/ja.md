```julia
get_nums_edges(
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}},
    conditions::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
