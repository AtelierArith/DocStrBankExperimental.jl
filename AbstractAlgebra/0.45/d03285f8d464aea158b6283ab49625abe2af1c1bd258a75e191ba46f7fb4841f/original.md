```
matrix(R::Ring, r::Int, c::Int, arr::AbstractVector{T}) where {T}
```

Constructs the $r \times c$ matrix over $R$, where the entries are taken row-wise from `arr`.
