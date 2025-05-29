```
resize_non_user_cache!(integrator::DEIntegrator,k::Int)
```

Resizes the non-user facing caches to be compatible with a DE of size `k`. This includes resizing Jacobian caches.

!!! note
    In many cases, [`resize!`](@ref) simply resizes [`full_cache`](@ref) variables and then calls this function. This finer control is required for some `AbstractArray` operations.

