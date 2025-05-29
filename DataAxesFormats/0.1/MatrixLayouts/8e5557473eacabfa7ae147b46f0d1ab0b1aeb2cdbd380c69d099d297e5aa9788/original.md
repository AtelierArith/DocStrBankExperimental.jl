```
require_major_axis(matrix::AbstractMatrix)::Int8
```

Similar to [`major_axis`](@ref) but will `error` if the matrix isn't in either row-major or column-major layout.
