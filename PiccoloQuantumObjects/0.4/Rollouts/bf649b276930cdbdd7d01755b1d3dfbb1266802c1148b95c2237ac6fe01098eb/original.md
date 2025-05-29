```
variational_unitary_rollout(
    Ũ⃗_init::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector{<:Real},
    system::VariationalQuantumSystem;
    show_progress::Bool=false,
    integrator::Function=expv,
    exp_vector_product::Bool=infer_is_evp(integrator)
)
variational_unitary_rollout(
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::VariationalQuantumSystem;
    kwargs...
)
variational_unitary_rollout(
    traj::NamedTrajectory,
    system::VariationalQuantumSystem;
    unitary_name::Symbol=:Ũ⃗,
    drive_name::Symbol=:a,
    kwargs...
)
```

Simulates the variational evolution of a quantum state under a given control trajectory.

# Returns

  * `Ũ⃗::Matrix{<:Real}`: The evolved unitary at each timestep.
  * `Ũ⃗_vars::Vector{<:Matrix{<:Real}}`: The variational derivatives of the  unitary with    respect to the variational parameters.

# Notes

This function computes the variational evolution of a unitary using the  variational generators of the system. It supports autodifferentiable controls and  timesteps, making it suitable for optimization tasks. The variational derivatives are  computed alongside the state evolution, enabling sensitivity analysis and gradient-based  optimization.
