```
nonsym(nbOne::Ti, size::Ti, diag_l::Ti, diag_u::Ti, spectrum::AbstractVector{Tv}, Am::SparseMatrixCSC{Tv2, Ti},) where {Tv<:Complex, Tv2<:Real, Ti<:Integer}
```

Generate a non symmetric matrix with default nilpotent matrix and user-provided initialization of matrix.

The usage of `nonsym` is the same as the one of `nonherm`, please refers to that part for more detais.

Please keep in mind the constraints of given spectrum vector and initialization of matrix, click [here](getting_started.md) for more details.
