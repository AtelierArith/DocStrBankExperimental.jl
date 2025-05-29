```
open_rollout(
    ρ⃗₁::AbstractVector{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem;
    kwargs...
)
```

Rollout a quantum state `ρ⃗₁` under the control `controls` for a time `Δt`

# Arguments

  * `ρ⃗₁::AbstractVector{<:Complex}`: Initial state vector
  * `controls::AbstractMatrix{<:Real}`: Control matrix
  * `Δt::AbstractVector`: Time steps
  * `system::OpenQuantumSystem`: Quantum system

# Keyword Arguments

  * `show_progress::Bool=false`: Show progress bar
  * `integrator::Function=expv`: Integrator function
  * `exp_vector_product::Bool`: Infer whether the integrator is an exponential-vector product
