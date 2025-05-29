```
UnitaryVariationalProblem(
    system::VariationalQuantumSystem,
    goal::AbstractPiccoloOperator,
    T::Int,
    Δt::Union{Float64, <:AbstractVector{Float64}};
    robust_times::AbstractVector{<:Union{AbstractVector{Int}, Nothing}}=[nothing for s ∈ system.G_vars],
    sensitive_times::AbstractVector{<:Union{AbstractVector{Int}, Nothing}}=[nothing for s ∈ system.G_vars],
    kwargs...
)
```

Constructs a unitary variational problem for optimizing quantum control trajectories.

# Arguments

  * `system::VariationalQuantumSystem`: The quantum system to be controlled, containing variational parameters.
  * `goal::AbstractPiccoloOperator`: The target operator or state to achieve at the end of the trajectory.
  * `T::Int`: The total number of timesteps in the trajectory.
  * `Δt::Union{Float64, <:AbstractVector{Float64}}`: The timestep duration or a vector of timestep durations.
  * `robust_times::AbstractVector`: Times at which robustness to variations in the trajectory is enforced.
  * `sensitive_times::AbstractVector`: Times at which sensitivity to variations in the trajectory is enhanced.
  * `unitary_integrator`: The integrator used for unitary evolution (default: `VariationalUnitaryIntegrator`).
  * `state_name::Symbol`: The name of the state variable in the trajectory (default: `:Ũ⃗`).
  * `variational_state_name::Symbol`: The name of the variational state variable (default: `:Ũ⃗ₐ`).
  * `variational_scales::AbstractVector`: Scaling factors for the variational state variables (default: `1.0`).
  * `control_name::Symbol`: The name of the control variable (default: `:a`).
  * `timestep_name::Symbol`: The name of the timestep variable (default: `:Δt`).
  * `init_trajectory::Union{NamedTrajectory, Nothing}`: An optional initial trajectory to start optimization.
  * `a_bound::Float64`: The bound for the control variable `a` (default: `1.0`).
  * `a_bounds::Vector`: Bounds for each control variable (default: filled with `a_bound`).
  * `da_bound::Float64`: The bound for the derivative of the control variable (default: `Inf`).
  * `da_bounds::Vector`: Bounds for each derivative of the control variable.
  * `dda_bound::Float64`: The bound for the second derivative of the control variable (default: `1.0`).
  * `dda_bounds::Vector`: Bounds for each second derivative of the control variable.
  * `Δt_min::Float64`: Minimum allowed timestep duration.
  * `Δt_max::Float64`: Maximum allowed timestep duration.
  * `Q::Float64`: Weight for the unitary infidelity objective (default: `100.0`).
  * `Q_v::Float64`: Weight for sensitivity objectives (default: `1.0`).
  * `R`: Regularization weight for control variables (default: `1e-2`).
  * `R_a`, `R_da`, `R_dda`: Regularization weights for control, its derivative, and second derivative.
  * `constraints::Vector`: Additional constraints for the optimization problem.
  * `piccolo_options::PiccoloOptions`: Options for configuring the Piccolo optimization framework.

# Returns

A `DirectTrajOptProblem` object representing the optimization problem, including the  trajectory, objective, integrators, and constraints.

# Notes

This function constructs a trajectory optimization problem for quantum control using  variational principles. It supports robust and sensitive trajectory design, regularization,  and optional constraints. The problem is solved using the Piccolo optimization framework.
