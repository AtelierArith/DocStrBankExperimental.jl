```julia
modelingtoolkitize(
    prob::SciMLBase.SDEProblem;
    kwargs...
) -> Union{Tuple{Any, Any, Any}, ModelingToolkit.SDESystem}

```

`SDEProblem`から`SDESystem`、従属変数、およびパラメータを生成します。
