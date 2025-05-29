```
lazy_map(f,::Type{T},a::AbstractArray...) where T
```

Like [`lazy_map(f,a::AbstractArray...)`](@ref), but the user provides the element type of the resulting array in order to circumvent type inference.
