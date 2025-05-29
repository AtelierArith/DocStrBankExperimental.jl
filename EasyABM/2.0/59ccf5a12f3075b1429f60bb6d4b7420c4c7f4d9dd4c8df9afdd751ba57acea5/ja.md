```julia
get_edges(
    model::EasyABM.GraphModel,
    condition::Function
) -> Union{Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#537#538"{EasyABM.GraphModel{S, T, G}, <:Function} where {S<:EasyABM.MType, T<:EasyABM.MType, G<:EasyABM.GType}), I<:(Base.Iterators.Flatten{I} where I<:(Base.Generator{Vector{Int64}, F} where F<:(EasyABM.var"#404#405"{EasyABM.DirPropGraph{S, G}} where {S<:EasyABM.MType, G<:EasyABM.DirGType})))}, Base.Iterators.Filter{F, I} where {F<:(EasyABM.var"#537#538"{EasyABM.GraphModel{S, T, G}, <:Function} where {S<:EasyABM.MType, T<:EasyABM.MType, G<:EasyABM.GType}), I<:(Base.Iterators.Flatten{I} where I<:(Base.Generator{Base.KeySet{Int64, Dict{Int64, Vector{Int64}}}, F} where F<:(EasyABM.var"#375#376"{EasyABM.SimplePropGraph{S, G}} where {S<:EasyABM.MType, G<:EasyABM.SimGType})))}}

```
