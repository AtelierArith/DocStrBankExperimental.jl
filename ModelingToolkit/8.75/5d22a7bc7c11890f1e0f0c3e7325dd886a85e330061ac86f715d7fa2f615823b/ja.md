```julia
modelingtoolkitize(
    prob::SciMLBase.ODEProblem;
    kwargs...
) -> Any

```

`ODESystem`、従属変数、およびパラメータを `ODEProblem` から生成します。
