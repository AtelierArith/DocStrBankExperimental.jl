```
rollout(
    ψ̃_init::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem
)
rollout(
    ψ_init::AbstractVector{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem
)
rollout(
    inits::AbstractVector{<:AbstractVector},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem
)
```

量子状態 `ψ̃_init` を制御 `controls` の下で時間 `Δt` の間、システム `system` を使用してロールアウトします。

`exp_vector_product` が `true` の場合、積分器は指数作用 `expv` のようなシグネチャを持つことが期待されます。そうでない場合は、`exp` のようなシグネチャを持つことが期待されます。

型は自動微分可能な制御と時間を許可する必要があります。
