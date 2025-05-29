```
block_diagonal_matrix(V::Vector{<:MatElem{T}}) where T <: NCRingElement
```

Create the block diagonal matrix whose blocks are given by the matrices in `V`. There must be at least one matrix in V.
