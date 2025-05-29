```julia
IntervalNonlinearFunctionExpr(
    sys::ModelingToolkit.NonlinearSystem;
    ...
) -> Expr
IntervalNonlinearFunctionExpr(
    sys::ModelingToolkit.NonlinearSystem,
    dvs;
    ...
) -> Expr
IntervalNonlinearFunctionExpr(
    sys::ModelingToolkit.NonlinearSystem,
    dvs,
    ps;
    ...
) -> Expr
IntervalNonlinearFunctionExpr(
    sys::ModelingToolkit.NonlinearSystem,
    dvs,
    ps,
    u0;
    p,
    linenumbers,
    kwargs...
) -> Expr

```

Create a Julia expression for an `IntervalNonlinearFunction` from the [`NonlinearSystem`](@ref). The arguments `dvs` and `ps` are used to set the order of the dependent variable and parameter vectors, respectively.
