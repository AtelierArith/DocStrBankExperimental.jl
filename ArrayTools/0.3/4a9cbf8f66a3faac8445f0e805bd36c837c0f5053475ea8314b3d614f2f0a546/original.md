```
same_size(A, B...) -> size(A)
```

checks whether arrays `A`, `B`, etc., all have the same size which is returned. A `DimensionMismatch` exception is thrown if array sizes are not all identical.

See also [`same_standard_size`](@ref), [`same_axes`](@ref).
