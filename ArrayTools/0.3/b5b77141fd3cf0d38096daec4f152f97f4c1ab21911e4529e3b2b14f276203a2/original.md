```
same_standard_size(A, B...) -> size(A)
```

checks whether arrays `A`, `B`, etc., all have standard indexing and the same size which is returned. If array sizes are not all identical, a `DimensionMismatch` exception is thrown. If arrays have non-standard indexing (that is indices not starting at index one), an `ArgumentError` exception is thrown.

See also [`standard_size`](@ref), [`has_standard_indexing`](@ref).
