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

[`NonlinearSystem`](@ref)から`IntervalNonlinearFunction`のためのJulia式を作成します。引数`dvs`と`ps`は、それぞれ従属変数とパラメータベクトルの順序を設定するために使用されます。
