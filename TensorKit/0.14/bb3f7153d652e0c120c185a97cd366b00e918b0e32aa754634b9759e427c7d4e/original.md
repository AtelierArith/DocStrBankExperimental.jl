```
numout(::Union{TT,Type{TT}}) where {TT<:AbstractTensorMap} -> Int
```

Return the number of output spaces of a tensor. This is equivalent to the number of spaces in the codomain of that tensor.

See also [`numin`](@ref) and [`numind`](@ref).
