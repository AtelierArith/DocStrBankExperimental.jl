```julia
create_similar(
    agent::EasyABM.GraphAgent{S<:EasyABM.MType, T<:EasyABM.MType}
) -> EasyABM.GraphAgent

```

Returns a list of n 2d agents all having same (other than _extras) properties as `agent`.  
