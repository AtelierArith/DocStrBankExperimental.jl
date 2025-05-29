```julia
IntervalNonlinearProblemExpr(
    sys::ModelingToolkit.NonlinearSystem,
    uspan::Tuple{T, T} where T;
    ...
) -> Expr
IntervalNonlinearProblemExpr(
    sys::ModelingToolkit.NonlinearSystem,
    uspan::Tuple{T, T} where T,
    parammap;
    kwargs...
) -> Expr

```

Generates a Julia expression for an IntervalNonlinearProblem from a NonlinearSystem and allows for automatically symbolically calculating numerical enhancements.
