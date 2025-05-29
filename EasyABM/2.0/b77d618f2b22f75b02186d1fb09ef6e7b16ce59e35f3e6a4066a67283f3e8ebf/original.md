```julia
get_nums_agents(
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.StaticType}, EasyABM.AbstractSpaceModel{EasyABM.StaticType}},
    conditions::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
