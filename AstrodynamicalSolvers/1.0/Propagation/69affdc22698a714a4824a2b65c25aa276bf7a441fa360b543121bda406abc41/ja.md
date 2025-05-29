```julia
propagate(
    orbit,
    Δt;
    stm,
    algorithm,
    reltol,
    abstol,
    kwargs...
)

```

軌道を時間的に前方（または後方）に数値的に積分し、提供された軌道と同一のパラメータを持つ新しい `AstrodynamicalOrbit` インスタンスを返します。
