```julia
generate_initializesystem(
    sys::ModelingToolkit.AbstractTimeDependentSystem;
    u0map,
    pmap,
    initialization_eqs,
    guesses,
    default_dd_guess,
    algebraic_only,
    check_units,
    check_defguess,
    name,
    kwargs...
) -> ModelingToolkit.NonlinearSystem

```

指定された初期条件から `AbstractTimeDependentSystem` の問題を初期化する `NonlinearSystem` を生成します。
