```
sparsity_pattern(result::AbstractColoringResult)
```

Return the matrix that was initially passed to [`coloring`](@ref), without any modifications.

!!! note
    This matrix is not necessarily a `SparseMatrixCSC`, nor does it necessarily have `Bool` entries.

