```
block_diagonal_matrix(R::NCRing, V::Vector{<:Matrix{T}}) where T <: NCRingElement
```

Create the block diagonal matrix over the ring `R` whose blocks are given by the matrices in `V`. Entries are coerced into `R` upon creation.
