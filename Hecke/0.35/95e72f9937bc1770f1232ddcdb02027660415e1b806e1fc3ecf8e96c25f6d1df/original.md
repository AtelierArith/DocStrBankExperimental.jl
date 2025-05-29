```
common_eigenspaces(L::Vector{<: MatElem{T}}; side::Symbol = :left)
  where T <: FieldElem -> Dict{Vector{T}, MatElem{T}}
```

Return a dictionary containing vectors of eigenvalues of the matrices in `L` as keys and the corresponding eigenspaces as values, that is, if `(k, v)` is a pair of a key and a value, then `v` is the eigenspace of `L[i]` w.r.t. the eigenvalue `k[i]` for all `i`. If side is `:right`, the right eigenspaces are computed, if it is `:left` then the left eigenspaces are computed.
