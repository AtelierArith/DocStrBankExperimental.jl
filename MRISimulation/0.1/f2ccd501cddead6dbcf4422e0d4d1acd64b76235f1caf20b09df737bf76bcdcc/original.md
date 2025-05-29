```
simulation(image::Array{T,2}, simParams::Dict) where T<:Union{Complex{<:AbstractFloat},AbstractFloat}
```

Simulate MRI raw data from given `image` data. All simulation parameters are passed to the function in the form of a dictionary.
