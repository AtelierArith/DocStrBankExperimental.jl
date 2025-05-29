```julia
modelingtoolkitize(
    prob::SciMLBase.NonlinearProblem;
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

Generate `NonlinearSystem`, dependent variables, and parameters from an `NonlinearProblem`.
