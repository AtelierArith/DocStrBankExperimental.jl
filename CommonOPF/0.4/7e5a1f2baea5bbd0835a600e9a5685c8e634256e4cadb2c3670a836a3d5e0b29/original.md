```
matrix_phases_to_vec(M::AbstractMatrix{T}, phases::AbstractVector{Int}) where T
```

Used in defining the KVL constraints, this method returns the entries of `M` at the indices in  `phases` in a vector.
