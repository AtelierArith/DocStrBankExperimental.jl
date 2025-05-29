```julia
struct TriMatrix{T, L<:TriMatrices.TriLayout, A} <: AbstractArray{T, 2}
```

A triangular or symmetric matrix which stores data non-redundantly in a contiguous linear array.
