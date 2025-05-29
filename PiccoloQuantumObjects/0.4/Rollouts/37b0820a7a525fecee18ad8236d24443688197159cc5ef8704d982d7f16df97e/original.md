```
rollout_fidelity(
    ψ̃_init::AbstractVector{<:Real},
    ψ̃_goal::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem
)
rollout_fidelity(
    ψ_init::AbstractVector{<:Complex},
    ψ_goal::AbstractVector{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem
)
rollout_fidelity(
    trajectory::NamedTrajectory,
    system::AbstractQuantumSystem
)
```

Calculate the fidelity between the final state of a rollout and a goal state.
