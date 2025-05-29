```julia
modelingtoolkitize(
    prob::SciMLBase.OptimizationProblem;
    u_names,
    p_names,
    kwargs...
) -> ModelingToolkit.OptimizationSystem

```

`OptimizationProblem`から`OptimizationSystem`、従属変数、およびパラメータを生成します。
