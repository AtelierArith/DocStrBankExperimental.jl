```julia
modelingtoolkitize(
    prob::SciMLBase.NonlinearProblem;
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

`NonlinearProblem`から`NonlinearSystem`、従属変数、およびパラメータを生成します。
