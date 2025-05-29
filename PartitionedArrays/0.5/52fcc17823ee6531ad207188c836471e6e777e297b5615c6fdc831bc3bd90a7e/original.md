```
local_values(a::PSparseMatrix)
```

Get a vector of matrices containing the local rows and columns in each part of `a`.

The row and column indices of the returned matrices can be mapped to global indices, own indices, ghost indices, and owner by using [`local_to_global`](@ref), [`local_to_own`](@ref), [`local_to_ghost`](@ref), and [`local_to_owner`](@ref), respectively.
