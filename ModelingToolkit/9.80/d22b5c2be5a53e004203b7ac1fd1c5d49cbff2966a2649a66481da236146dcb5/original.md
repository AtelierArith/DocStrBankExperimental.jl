```julia
modelingtoolkitize(
    prob::Union{SciMLBase.NonlinearLeastSquaresProblem, SciMLBase.NonlinearProblem};
    u_names,
    p_names,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

Generate `NonlinearSystem`, dependent variables, and parameters from an `NonlinearProblem`.
