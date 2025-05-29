```
VectorQuantity{T}
```

Type union representing one-dimensional arrays with elements of type `T`, with or without a physical unit.

Alias for `Union{Vector{T}, AbstractQuantityArray{T, 1}} where T<:Number`.
