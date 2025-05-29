```julia
ImplicitDiscreteProblem(
    sys::ModelingToolkit.ImplicitDiscreteSystem;
    ...
) -> SciMLBase.ImplicitDiscreteProblem{_A, _B, true, _C, SciMLBase.ImplicitDiscreteFunction{iip, specialize, F, Ta, O, SYS, RP, ID}, Base.Pairs{K, V, I, A}} where {_A, _B, _C, iip, specialize, F, Ta, O, SYS, RP, ID, K, V, I, A}
ImplicitDiscreteProblem(
    sys::ModelingToolkit.ImplicitDiscreteSystem,
    u0map;
    ...
) -> SciMLBase.ImplicitDiscreteProblem{_A, _B, true, _C, SciMLBase.ImplicitDiscreteFunction{iip, specialize, F, Ta, O, SYS, RP, ID}, Base.Pairs{K, V, I, A}} where {_A, _B, _C, iip, specialize, F, Ta, O, SYS, RP, ID, K, V, I, A}
ImplicitDiscreteProblem(
    sys::ModelingToolkit.ImplicitDiscreteSystem,
    u0map,
    tspan;
    ...
) -> Any
ImplicitDiscreteProblem(
    sys::ModelingToolkit.ImplicitDiscreteSystem,
    u0map,
    tspan,
    parammap;
    eval_module,
    eval_expression,
    kwargs...
) -> Any

```

Generates an ImplicitDiscreteProblem from an ImplicitDiscreteSystem.
