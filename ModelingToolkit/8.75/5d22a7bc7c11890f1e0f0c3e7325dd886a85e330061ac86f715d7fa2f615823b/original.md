```julia
modelingtoolkitize(
    prob::SciMLBase.ODEProblem;
    kwargs...
) -> Any

```

Generate `ODESystem`, dependent variables, and parameters from an `ODEProblem`.
