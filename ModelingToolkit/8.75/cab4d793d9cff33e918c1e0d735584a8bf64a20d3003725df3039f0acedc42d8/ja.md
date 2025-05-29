```julia
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem;
    ...
) -> Any
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem,
    u0map;
    ...
) -> Any
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem,
    u0map,
    tspan;
    ...
) -> Any
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem,
    u0map,
    tspan,
    parammap;
    eval_module,
    eval_expression,
    use_union,
    kwargs...
) -> Any

```

DiscreteSystemからDiscreteProblemを生成します。
