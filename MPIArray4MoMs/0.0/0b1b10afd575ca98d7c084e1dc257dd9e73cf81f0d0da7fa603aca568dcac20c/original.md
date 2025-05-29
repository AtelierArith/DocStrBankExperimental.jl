```
ArrayChunk{T, N} <:AbstractArray{T, N}
```

Array chunk with custom indices.

```
data::Array{T, N}
indices::NTuple{N, Union{UnitRange{Int}, Vector{Int}}}
```
