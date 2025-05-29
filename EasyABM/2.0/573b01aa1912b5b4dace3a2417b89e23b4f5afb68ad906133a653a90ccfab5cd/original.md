```julia
create_similar(
    agent::EasyABM.Agent2D{S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType},
    n::Int64
) -> Array{EasyABM.Agent2D{S, P, T}, 1} where {S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType}

```

Returns a list of n 2d agents all having same (other than _extras) properties as `agent` if `agent` is alive.  
