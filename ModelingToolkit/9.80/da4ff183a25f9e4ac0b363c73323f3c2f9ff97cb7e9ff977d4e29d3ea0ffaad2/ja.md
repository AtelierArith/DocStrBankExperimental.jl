```julia
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem;
    ...
) -> SciMLBase.DiscreteProblem{_A, _B, true, _C, SciMLBase.DiscreteFunction{iip, specialize, F, Ta, O, SYS, ID}, Base.Pairs{Symbol, Union{}, Tuple{}, @NamedTuple{}}} where {_A, _B, _C, iip, specialize, F, Ta, O, SYS, ID}
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem,
    u0map;
    ...
) -> SciMLBase.DiscreteProblem{_A, _B, true, _C, SciMLBase.DiscreteFunction{iip, specialize, F, Ta, O, SYS, ID}, Base.Pairs{Symbol, Union{}, Tuple{}, @NamedTuple{}}} where {_A, _B, _C, iip, specialize, F, Ta, O, SYS, ID}
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem,
    u0map,
    tspan;
    ...
) -> SciMLBase.DiscreteProblem{_A, _B, true, _C, SciMLBase.DiscreteFunction{iip, specialize, F, Ta, O, SYS, ID}, Base.Pairs{Symbol, Union{}, Tuple{}, @NamedTuple{}}} where {_A, _B, _C, iip, specialize, F, Ta, O, SYS, ID}
DiscreteProblem(
    sys::ModelingToolkit.DiscreteSystem,
    u0map,
    tspan,
    parammap;
    eval_module,
    eval_expression,
    kwargs...
) -> SciMLBase.DiscreteProblem{_A, _B, true, _C, SciMLBase.DiscreteFunction{iip, specialize, F, Ta, O, SYS, ID}, Base.Pairs{Symbol, Union{}, Tuple{}, @NamedTuple{}}} where {_A, _B, _C, iip, specialize, F, Ta, O, SYS, ID}

```

DiscreteSystemからDiscreteProblemを生成します。
