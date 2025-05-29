```
simulation(image::Array{T,3}, simParams::Dict, filename::String) where T<:Union{Complex{<:AbstractFloat},AbstractFloat}
```

Performs the same simulation as `simulation(image, simParams)` and saves the result in a file with name `filename`
