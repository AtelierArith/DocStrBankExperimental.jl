```julia
create_similar(
    agent::EasyABM.GraphAgent{S<:EasyABM.MType, T<:EasyABM.MType},
    n::Int64
) -> Array{EasyABM.GraphAgent{S, T}, 1} where {S<:EasyABM.MType, T<:EasyABM.MType}

```

Returns a list of n 2d agents all having same (other than _extras) properties as `agent`.  
