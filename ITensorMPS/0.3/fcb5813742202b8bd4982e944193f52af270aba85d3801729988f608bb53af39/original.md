```
random_mps(sites::Vector{<:Index}; linkdims=1)
random_mps(eltype::Type{<:Number}, sites::Vector{<:Index}; linkdims=1)
```

Construct a random MPS with link dimension `linkdims` which by default has element type `Float64`.

`linkdims` can also accept a `Vector{Int}` with `length(linkdims) == length(sites) - 1` for constructing an MPS with non-uniform bond dimension.
