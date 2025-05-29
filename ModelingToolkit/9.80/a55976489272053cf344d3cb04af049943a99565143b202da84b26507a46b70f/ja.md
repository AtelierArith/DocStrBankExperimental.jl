```julia
modelingtoolkitize(
    prob::SciMLBase.OptimizationProblem;
    u_names,
    p_names,
    kwargs...
) -> ModelingToolkit.OptimizationSystem

```

`OptimizationSystem`、従属変数、およびパラメータを`OptimizationProblem`から生成します。
