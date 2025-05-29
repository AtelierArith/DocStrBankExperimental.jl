```julia
modelingtoolkitize(
    prob::SciMLBase.OptimizationProblem;
    kwargs...
) -> ModelingToolkit.OptimizationSystem

```

Generate `OptimizationSystem`, dependent variables, and parameters from an `OptimizationProblem`.
