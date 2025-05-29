```
MatrixQuantity{T}
```

Type union representing two-dimensional arrays with elements of type `T`, with or without a physical unit.

Alias for `Union{Matrix{T}, AbstractQuantityArray{T, 2}} where T<:Number`.
