```
ghost_values(a::PVector)
```

Get a vector of vectors containing the ghost values in each part of `a`.

The indices of the returned matrices can be mapped to global indices, local indices, and owner by using [`ghost_to_global`](@ref), [`ghost_to_local`](@ref), and [`ghost_to_owner`](@ref), respectively.
