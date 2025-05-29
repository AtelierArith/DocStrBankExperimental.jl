```julia
propagate!(
    orbit,
    Δt;
    stm,
    algorithm,
    reltol,
    abstol,
    kwargs...
)

```

軌道を時間的に前方（または後方）に数値的に積分し、`AstrodynamicalOrbit` インスタンス内の状態ベクトルをその場で修正します。
