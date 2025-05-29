```julia
get_nums_agents(
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.MortalType}, EasyABM.AbstractSpaceModel{EasyABM.MortalType}},
    conditions::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
