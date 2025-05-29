```
open_rollout(
    ρ₁::AbstractMatrix{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem;
    kwargs...
)
```

密度行列 `ρ₁` を制御 `controls` と時間ステップ `Δt` の下で展開します。
