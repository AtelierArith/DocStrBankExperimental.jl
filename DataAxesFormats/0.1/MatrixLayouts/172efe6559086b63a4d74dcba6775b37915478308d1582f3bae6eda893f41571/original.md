```
require_minor_axis(matrix::AbstractMatrix)::Int8
```

Similar to [`minor_axis`](@ref) but will `error` if the matrix isn't in either row-major or column-major layout.
