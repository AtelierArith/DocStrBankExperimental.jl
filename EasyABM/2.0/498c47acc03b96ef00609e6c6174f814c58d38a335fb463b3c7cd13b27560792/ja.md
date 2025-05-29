```julia
get_agents_avg_props(
    model::Union{EasyABM.AbstractGraphModel{T<:EasyABM.MType, EasyABM.MortalType}, EasyABM.AbstractSpaceModel{EasyABM.MortalType}},
    props::Function...;
    labels,
    plot_result
) -> DataFrames.DataFrame

```
