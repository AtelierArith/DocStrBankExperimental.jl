```
basis_to_array_index(B::AbstractBSplineBasis, axs, i::Int) -> Int
```

Converts from a basis index `i` (for basis function $b_i$) to a valid index in an array `A` with indices `axs`, where `axs` is typically the result of `axes(A, dim)` for a given dimension `dim`.

This is mainly relevant for periodic bases, in which case `i` may be outside of the "main" period of the basis.

It is *assumed* that `length(B) == length(axs)` (this is not checked by this function).
