```
orthogonalize!(M::MPS, j::Int; kwargs...)
orthogonalize(M::MPS, j::Int; kwargs...)

orthogonalize!(M::MPO, j::Int; kwargs...)
orthogonalize(M::MPO, j::Int; kwargs...)
```

Move the orthogonality center of the MPS to site `j`. No observable property of the MPS will be changed, and no truncation of the bond indices is performed. Afterward, tensors `1,2,...,j-1` will be left-orthogonal and tensors `j+1,j+2,...,N` will be right-orthogonal.

Either modify in-place with `orthogonalize!` or out-of-place with `orthogonalize`.
