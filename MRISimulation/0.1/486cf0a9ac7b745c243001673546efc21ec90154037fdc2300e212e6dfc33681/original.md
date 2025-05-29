```
simulation(image::Array{T,3}, simParams::Dict) where T<:Complex{<:AbstractFloat}
```

Simulate MRI raw data from given `image` data. All simulation parameters are passed to the function in the form of a dictionary.
