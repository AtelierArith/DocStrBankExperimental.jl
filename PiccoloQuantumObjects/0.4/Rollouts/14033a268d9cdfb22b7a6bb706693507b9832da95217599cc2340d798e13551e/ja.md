```
open_rollout(
    ρ₁::AbstractMatrix{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem;
    kwargs...
)
```

制御 `controls` と時間ステップ `Δt` の下で密度行列 `ρ₁` を展開します。
