```julia
create_similar(
    agent::EasyABM.Agent2D{S<:Union{Float64, Int64}, P<:EasyABM.SType, T<:EasyABM.MType}
) -> EasyABM.Agent2D

```

Returns an agent with same (other than _extras) properties as given `agent`. 
