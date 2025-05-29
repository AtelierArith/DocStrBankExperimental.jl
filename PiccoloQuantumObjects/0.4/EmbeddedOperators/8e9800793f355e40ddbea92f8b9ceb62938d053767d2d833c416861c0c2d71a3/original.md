```
unembed(matrix::AbstractMatrix{<:Number}, subspace::AbstractVector{Int})
```

Unembed a subspace operator from the `matrix`. This is equivalent to calling `matrix[subspace, subspace]`.
