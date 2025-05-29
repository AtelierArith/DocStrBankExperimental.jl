```julia
create_similar(
    agent::EasyABM.Agent3D{S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType},
    n::Int64
) -> Array{EasyABM.Agent3D{S, P, T}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType}

```

Returns a list of n 2d agents all having same properties as `agent`.  
