```
ArrayQuantity{T,N}
```

Type union representing `N`-dimensional arrays with elements of type `T`, with or without a physical unit.

Alias for `Union{Array{T,N}, AbstractQuantityArray{T,N}} where {T<:Number, N}`.
