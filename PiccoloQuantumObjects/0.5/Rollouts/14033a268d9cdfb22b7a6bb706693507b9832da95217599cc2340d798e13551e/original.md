```
open_rollout(
    ρ₁::AbstractMatrix{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem;
    kwargs...
)
```

Rollout a density matrix `ρ₁` under the control `controls` and timesteps `Δt`
