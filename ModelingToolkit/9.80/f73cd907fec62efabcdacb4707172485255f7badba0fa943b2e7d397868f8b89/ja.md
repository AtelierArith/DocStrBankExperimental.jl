```julia
modelingtoolkitize(
    prob::SciMLBase.ODEProblem;
    u_names,
    p_names,
    kwargs...
) -> Any

```

`ODEProblem`から`ODESystem`、従属変数、およびパラメータを生成します。
