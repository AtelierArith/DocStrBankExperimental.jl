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

Rollout a quantum state `ψ̃_init` under the control `controls` for a time `Δt` using the system `system`.

If `exp_vector_product` is `true`, the integrator is expected to have a signature like the exponential action, `expv`. Otherwise, it is expected to have a signature like `exp`.

Types should allow for autodifferentiable controls and times.
