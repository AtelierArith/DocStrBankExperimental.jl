```
ghost_ghost_values(a::PSparseMatrix)
```

Get a vector of matrices containing the ghost rows and columns in each part of `a`.

The row and column indices of the returned matrices can be mapped to global indices, local indices, and owner by using [`ghost_to_global`](@ref), [`ghost_to_local`](@ref), and [`ghost_to_owner`](@ref), respectively.
