```
get_u0(res, prob::PEtabODEProblem; kwargs...)
```

Retrieve the `ODEProblem` initial values for simulating the ODE model in `prob`. `res` can be a parameter estimation result (e.g., `PEtabMultistartResult`) or a `Vector` with parameters in the order expected by `prob` (see [`get_x`](@ref)).

For information on keyword arguements see [`get_ps`](@ref).

See also [`get_odeproblem`](@ref) and [`get_odesol`](@ref).
