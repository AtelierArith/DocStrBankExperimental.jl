```julia
agents_at(
    node,
    model::EasyABM.GraphModel{EasyABM.MortalType, T<:EasyABM.MType}
) -> Union{Base.Generator{I, typeof(identity)} where I<:(Array{EasyABM.GraphAgent{EasyABM.MortalType, T}, 1} where T<:EasyABM.MType), Base.Generator{_A, F} where {_A, F<:(EasyABM.var"#541#542"{EasyABM.GraphModel{EasyABM.MortalType, T, G}} where {T<:EasyABM.MType, G<:EasyABM.GType})}}

```

Returns list of agents at a given node. 
