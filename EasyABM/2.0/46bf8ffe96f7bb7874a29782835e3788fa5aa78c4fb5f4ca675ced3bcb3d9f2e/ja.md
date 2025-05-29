```julia
get_agents_avg_props(
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.StaticType}, EasyABM.AbstractSpaceModel{EasyABM.StaticType}},
    props::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
