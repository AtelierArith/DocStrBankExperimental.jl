```julia
get_agents(
    model::EasyABM.GraphModel{T<:EasyABM.MType, EasyABM.MortalType},
    condition::Function
) -> Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#546#548"{<:Function}), I<:(Base.Iterators.Flatten{I} where I<:(Base.Generator{UnitRange{Int64}, F} where F<:EasyABM.var"#545#547"))}

```
