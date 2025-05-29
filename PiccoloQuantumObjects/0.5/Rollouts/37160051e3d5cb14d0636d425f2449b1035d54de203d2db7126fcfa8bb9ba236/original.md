```
open_rollout_fidelity(
    ρ⃗₁::AbstractVector{<:Complex},
    ρ⃗₂::AbstractVector{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem
)
open_rollout_fidelity(
    ρ₁::AbstractMatrix{<:Complex},
    ρ₂::AbstractMatrix{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem
)
open_rollout_fidelity(
    traj::NamedTrajectory,
    system::OpenQuantumSystem;
    state_name::Symbol=:ρ⃗̃,
    control_name::Symbol=:a,
    kwargs...
)
```

Calculate the fidelity between the final state of an open quantum system rollout and a goal state.
