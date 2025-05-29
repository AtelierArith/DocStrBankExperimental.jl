```
get_system(res, prob::PEtabODEProblem; kwargs...) -> (sys, p, u0, callbacks)
```

Retrieve the dynamic model system, parameter map (`p`), initial species map (`u0`), and callbacks (`CallbackSet`) for the model in `prob`. The argument `res` can be a parameter estimation result (e.g., `PEtabMultistartResult`) or a `Vector` of parameters in the order expected by `prob` (see [`get_x`](@ref)).

The system type returned depends on the input to `PEtabModel`. If the model is provided as a `ReactionSystem`, a `ReactionSystem` is returned. The same applies for an `ODESystem`. If the model is provided via an SBML file, a `ReactionSystem` is returned.

For information on keyword arguments, see [`get_ps`](@ref).

See also: [`get_u0`](@ref) and [`get_odesol`](@ref).
