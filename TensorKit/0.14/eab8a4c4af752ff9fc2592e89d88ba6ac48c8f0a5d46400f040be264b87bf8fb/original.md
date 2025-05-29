```
numind(::Union{T,Type{T}}) where {T<:AbstractTensorMap} -> Int
```

Return the total number of input and output spaces of a tensor. This is equivalent to the total number of spaces in the domain and codomain of that tensor.

See also [`numout`](@ref) and [`numin`](@ref).
