```julia
modelingtoolkitize(
    prob::SciMLBase.OptimizationProblem;
    kwargs...
) -> ModelingToolkit.OptimizationSystem

```

`OptimizationProblem` から `OptimizationSystem`、従属変数、およびパラメータを生成します。
