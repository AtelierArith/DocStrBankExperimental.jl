```
rows(A::AbstractSparseMatrixCOO)
```

Return a vector of the row indices of `A`. Any modifications to the returned vector will mutate `A` as well. Providing access to how the row indices are stored internally can be useful in conjunction with iterating over structural nonzero values. See also [`nonzeros`](@ref).
