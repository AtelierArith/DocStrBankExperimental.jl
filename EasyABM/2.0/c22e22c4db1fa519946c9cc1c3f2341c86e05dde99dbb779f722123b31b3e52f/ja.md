```julia
get_nodes(
    model::EasyABM.GraphModel,
    condition::Function
) -> Base.Iterators.Filter{F} where F<:(EasyABM.var"#533#534"{EasyABM.GraphModel{S, T, G}, <:Function} where {S<:EasyABM.MType, T<:EasyABM.MType, G<:EasyABM.GType})

```
