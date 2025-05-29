```
relayout(matrix::AbstractMatrix)::AbstractMatrix
relayout(matrix::NamedMatrix)::NamedMatrix
```

Same as [`relayout!`](@ref) but allocates the destination matrix for you. Is equivalent to `transpose(transposer(matrix))`.
