```julia
PDESystem(
;
    A,
    b,
    bc,
    DI,
    qdim,
    Factors,
    SystemMatrix,
    B,
    state,
    rhs
) -> MinFEM.PDESystem

```

[PDESystem](@ref) のコンストラクタ。キーワード引数で全てのフィールドを指定することができます。
