```
unitary_rollout(
    Ũ⃗_init::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem;
    kwargs...
)
```

Rollout a isomorphic unitary operator `Ũ⃗_init` under the control `controls` for a time `Δt` using the system `system`.

# Arguments

  * `Ũ⃗_init::AbstractVector{<:Real}`: Initial unitary vector
  * `controls::AbstractMatrix{<:Real}`: Control matrix
  * `Δt::AbstractVector`: Time steps
  * `system::AbstractQuantumSystem`: Quantum system

# Keyword Arguments

  * `show_progress::Bool=false`: Show progress bar
  * `integrator::Function=expv`: Integrator function
  * `exp_vector_product::Bool`: Infer whether the integrator is an exponential-vector product
