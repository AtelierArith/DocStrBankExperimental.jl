```
get_odeproblem(res, prob::PEtabODEProblem; kwargs...) -> (sys, callbacks)
```

Retrieve the `ODEProblem` and callbacks (`CallbackSet`) for simulating the ODE model in `prob`. `res` can be a parameter estimation result (e.g., `PEtabMultistartResult`) or a `Vector` with parameters in the order expected by `prob` (see [`get_x`](@ref)).

For information on keyword arguements see [`get_ps`](@ref).

See also: [`get_u0`](@ref) and [`get_odesol`](@ref).
