```julia
initializesystem(
    sys::ModelingToolkit.ODESystem;
    name,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

指定された初期条件からODE問題を初期化する`NonlinearSystem`を生成します。
