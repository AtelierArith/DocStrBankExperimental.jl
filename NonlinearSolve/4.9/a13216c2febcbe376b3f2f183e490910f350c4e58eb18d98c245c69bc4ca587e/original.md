```
FastShortcutNLLSPolyalg(
    ::Type{T} = Float64;
    concrete_jac = nothing,
    linsolve = nothing,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

A polyalgorithm focused on balancing speed and robustness. It first tries less robust methods for more performance and then tries more robust techniques if the faster ones fail.

### Arguments

  * `T`: The eltype of the initial guess. It is only used to check if some of the algorithms are compatible with the problem type. Defaults to `Float64`.
