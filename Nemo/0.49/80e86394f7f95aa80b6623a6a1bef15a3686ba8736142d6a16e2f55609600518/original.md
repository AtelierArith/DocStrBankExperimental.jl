```
eigenvalues_with_multiplicities(M::MatElem{T}) where T <: FieldElem
```

Return the eigenvalues of `M` (which lie in `base_ring(M)`) together with their algebraic multiplicities as a vector of tuples of (root, multiplicity).
