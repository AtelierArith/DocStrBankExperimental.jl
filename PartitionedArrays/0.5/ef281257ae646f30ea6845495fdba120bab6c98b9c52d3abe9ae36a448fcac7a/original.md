```
local_values(a::PVector)
```

Get a vector of vectors containing the local values in each part of `a`.

The indices of the returned vectors can be mapped to global indices, own indices, ghost indices, and owner by using [`local_to_global`](@ref), [`local_to_own`](@ref), [`local_to_ghost`](@ref), and [`local_to_owner`](@ref), respectively.
