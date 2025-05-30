```
deleteat_non_user_cache!(integrator::DEIntegrator,idxs)
```

[`deleteat!`](@ref)s the non-user facing caches at indices `idxs`. This includes resizing Jacobian caches.

!!! note
    In many cases, `deleteat!` simply `deleteat!`s [`full_cache`](@ref) variables and then calls this function. This finer control is required for some `AbstractArray` operations.

