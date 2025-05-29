```julia
modelingtoolkitize(
    prob::SciMLBase.ODEProblem;
    u_names,
    p_names,
    kwargs...
) -> Any

```

Generate `ODESystem`, dependent variables, and parameters from an `ODEProblem`.
