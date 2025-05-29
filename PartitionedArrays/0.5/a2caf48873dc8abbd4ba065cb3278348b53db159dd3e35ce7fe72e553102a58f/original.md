```
ghost_own_values(a::PSparseMatrix)
```

Get a vector of matrices containing the ghost rows and own columns in each part of `a`.

The *row* indices of the returned matrices can be mapped to global indices, local indices, and owner by using [`ghost_to_global`](@ref), [`ghost_to_local`](@ref), and [`ghost_to_owner`](@ref), respectively.

The *column* indices of the returned matrices can be mapped to global indices, local indices, and owner by using [`own_to_global`](@ref), [`own_to_local`](@ref), and [`own_to_owner`](@ref), respectively.
