```julia
get_agents(
    model::EasyABM.GraphModel{T<:EasyABM.MType, EasyABM.StaticType},
    condition::Function
) -> Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#553#554"{<:Function}), I<:(Array{EasyABM.GraphAgent{T, EasyABM.StaticType}, 1} where T<:EasyABM.MType)}

```
