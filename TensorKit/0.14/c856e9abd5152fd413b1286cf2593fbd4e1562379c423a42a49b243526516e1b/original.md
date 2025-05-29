```
randisometry([::Type{T}=Float64], dims::Dims{2}) -> Array{T,2}
randhaar([::Type{T}=Float64], dims::Dims{2}) -> Array{T,2}
```

Create a random isometry of size `dims`, uniformly distributed according to the Haar measure.

See also [`randuniform`](@ref) and [`randnormal`](@ref).
