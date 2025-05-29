```
addat_non_user_cache!(i::DEIntegrator,idxs)
```

[`addat!`](@ref)s the non-user facing caches at indices `idxs`. This includes resizing Jacobian caches.

!!! note
    In many cases, `addat!` simply `addat!`s [`full_cache`](@ref) variables and then calls this function. This finer control is required for some `AbstractArray` operations.

