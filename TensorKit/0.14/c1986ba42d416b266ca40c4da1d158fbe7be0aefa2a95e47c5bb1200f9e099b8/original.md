```
numin(::Union{TT,Type{TT}}) where {TT<:AbstractTensorMap} -> Int
```

Return the number of input spaces of a tensor. This is equivalent to the number of spaces in the domain of that tensor.

See also [`numout`](@ref) and [`numind`](@ref).
