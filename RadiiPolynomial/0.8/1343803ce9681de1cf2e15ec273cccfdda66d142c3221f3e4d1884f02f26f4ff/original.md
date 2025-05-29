```
TensorIndices{<:Tuple}
```

Multidimentional rectangular range of indices for some [`TensorSpace`](@ref).

# Examples

```jldoctest
julia> TensorIndices((0:2, -1:1))
TensorIndices{Tuple{UnitRange{Int64}, UnitRange{Int64}}}((0:2, -1:1))

julia> indices(Taylor(2) ⊗ Fourier(1, 1.0))
TensorIndices{Tuple{UnitRange{Int64}, UnitRange{Int64}}}((0:2, -1:1))
```
