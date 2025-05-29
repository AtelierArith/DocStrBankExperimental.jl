```
own_values(a::PVector)
```

Get a vector of vectors containing the own values in each part of `a`.

The indices of the returned vectors can be mapped to global indices, local indices, and owner by using [`own_to_global`](@ref), [`own_to_local`](@ref), and [`own_to_owner`](@ref), respectively.
