```julia
modelingtoolkitize(
    prob::Union{SciMLBase.NonlinearLeastSquaresProblem, SciMLBase.NonlinearProblem};
    u_names,
    p_names,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

`NonlinearSystem`、従属変数、およびパラメータを`NonlinearProblem`から生成します。
