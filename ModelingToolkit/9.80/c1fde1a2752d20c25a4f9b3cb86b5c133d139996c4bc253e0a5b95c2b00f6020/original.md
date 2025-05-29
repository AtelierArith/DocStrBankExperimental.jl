```julia
IntervalNonlinearFunction(
    sys::ModelingToolkit.NonlinearSystem;
    ...
) -> SciMLBase.IntervalNonlinearFunction{false, SciMLBase.FullSpecialize, ModelingToolkit.GeneratedFunctionWrapper{_A, _B, Nothing}, Nothing, ModelingToolkit.ObservedFunctionCache{ModelingToolkit.NonlinearSystem}, ModelingToolkit.NonlinearSystem, Nothing} where {_A, _B}
IntervalNonlinearFunction(
    sys::ModelingToolkit.NonlinearSystem,
    dvs;
    ...
) -> SciMLBase.IntervalNonlinearFunction{false, SciMLBase.FullSpecialize, ModelingToolkit.GeneratedFunctionWrapper{_A, _B, Nothing}, Nothing, ModelingToolkit.ObservedFunctionCache{ModelingToolkit.NonlinearSystem}, ModelingToolkit.NonlinearSystem, Nothing} where {_A, _B}
IntervalNonlinearFunction(
    sys::ModelingToolkit.NonlinearSystem,
    dvs,
    ps;
    ...
) -> SciMLBase.IntervalNonlinearFunction{false, SciMLBase.FullSpecialize, ModelingToolkit.GeneratedFunctionWrapper{_A, _B, Nothing}, Nothing, ModelingToolkit.ObservedFunctionCache{ModelingToolkit.NonlinearSystem}, ModelingToolkit.NonlinearSystem, Nothing} where {_A, _B}
IntervalNonlinearFunction(
    sys::ModelingToolkit.NonlinearSystem,
    dvs,
    ps,
    u0;
    p,
    eval_expression,
    eval_module,
    initialization_data,
    kwargs...
) -> SciMLBase.IntervalNonlinearFunction{false, SciMLBase.FullSpecialize, ModelingToolkit.GeneratedFunctionWrapper{_A, _B, Nothing}, Nothing, ModelingToolkit.ObservedFunctionCache{ModelingToolkit.NonlinearSystem}, ModelingToolkit.NonlinearSystem, Nothing} where {_A, _B}

```

Create an `IntervalNonlinearFunction` from the [`NonlinearSystem`](@ref). The arguments `dvs` and `ps` are used to set the order of the dependent variable and parameter vectors, respectively.
