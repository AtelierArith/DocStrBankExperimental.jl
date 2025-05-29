```
variational_rollout(
    ψ̃_init::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector{<:Real},
    system::VariationalQuantumSystem;
    show_progress::Bool=false,
    integrator::Function=expv,
    exp_vector_product::Bool=infer_is_evp(integrator)
)
variational_rollout(ψ::Vector{<:Complex}, args...; kwargs...)
variational_rollout(inits::AbstractVector{<:AbstractVector}, args...; kwargs...)
variational_rollout(
    traj::NamedTrajectory, 
    system::AbstractQuantumSystem; 
    state_name::Symbol=:ψ̃,
    drive_name::Symbol=:a,
    kwargs...
)
```

Simulates the variational evolution of a quantum state under a given control trajectory.

# Returns

  * `Ψ̃::Matrix{<:Real}`: The evolved quantum state at each timestep.
  * `Ψ̃_vars::Vector{<:Matrix{<:Real}}`: The variational derivatives of the    quantum state with respect to the variational parameters.

# Notes

This function computes the variational evolution of a quantum state using the  variational generators of the system. It supports autodifferentiable controls and  timesteps, making it suitable for optimization tasks. The variational derivatives are  computed alongside the state evolution, enabling sensitivity analysis and gradient-based  optimization.
