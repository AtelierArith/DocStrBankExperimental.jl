```julia
modelingtoolkitize(
    prob::SciMLBase.OptimizationProblem;
    u_names,
    p_names,
    kwargs...
) -> ModelingToolkit.OptimizationSystem

```

Generate `OptimizationSystem`, dependent variables, and parameters from an `OptimizationProblem`.
