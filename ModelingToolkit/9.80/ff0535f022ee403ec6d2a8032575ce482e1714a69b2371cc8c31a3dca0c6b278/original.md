```julia
modelingtoolkitize(
    prob::SciMLBase.SDEProblem;
    kwargs...
) -> Union{Tuple{Any, Any, Any}, ModelingToolkit.SDESystem}

```

Generate `SDESystem`, dependent variables, and parameters from an `SDEProblem`.
