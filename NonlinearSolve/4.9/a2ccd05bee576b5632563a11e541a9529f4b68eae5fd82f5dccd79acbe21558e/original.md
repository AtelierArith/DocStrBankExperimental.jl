```
FastShortcutNonlinearPolyalg(
    ::Type{T} = Float64;
    concrete_jac = nothing,
    linsolve = nothing,
    must_use_jacobian::Val = Val(false),
    prefer_simplenonlinearsolve::Val = Val(false),
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing,
    u0_len::Union{Int, Nothing} = nothing
) where {T}
```

A polyalgorithm focused on balancing speed and robustness. It first tries less robust methods for more performance and then tries more robust techniques if the faster ones fail.

### Arguments

  * `T`: The eltype of the initial guess. It is only used to check if some of the algorithms are compatible with the problem type. Defaults to `Float64`.

### Keyword Arguments

  * `u0_len`: The length of the initial guess. If this is `nothing`, then the length of the initial guess is not checked. If this is an integer and it is less than `25`, we use jacobian based methods.
