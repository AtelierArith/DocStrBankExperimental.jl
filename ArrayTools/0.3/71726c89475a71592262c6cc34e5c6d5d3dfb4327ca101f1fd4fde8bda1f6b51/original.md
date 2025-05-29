```
same_axes(A, B...) -> axes(A)
```

checks whether arrays `A`, `B`, etc., have the same axes and returns them. A `DimensionMismatch` exception is thrown if axes are not all identical.

See also [`same_size`](@ref), [`all_indices`](@ref).
