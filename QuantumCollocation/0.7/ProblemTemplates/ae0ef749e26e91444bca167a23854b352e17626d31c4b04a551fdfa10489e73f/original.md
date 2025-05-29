```
UnitarySamplingProblem(systemns, operator, T, Δt; kwargs...)
```

A `UnitarySamplingProblem` is a quantum control problem where the goal is to find a control pulse that generates a target unitary operator for a set of quantum systems. The controls are shared among all systems, and the optimization seeks to find the control  pulse that achieves the operator for each system. The idea is to enforce a robust solution by including multiple systems reflecting the problem uncertainty.

# Arguments

  * `systems::AbstractVector{<:AbstractQuantumSystem}`: A vector of quantum systems.
  * `operators::AbstractVector{<:AbstractPiccoloOperator}`: A vector of target operators.
  * `T::Int`: The number of time steps.
  * `Δt::Union{Float64, Vector{Float64}}`: The time step value or vector of time steps.

# Keyword Arguments

  * `system_labels::Vector{String} = string.(1:length(systems))`: The labels for each system.
  * `system_weights::Vector{Float64} = fill(1.0, length(systems))`: The weights for each system.
  * `init_trajectory::Union{NamedTrajectory, Nothing} = nothing`: The initial trajectory.
  * `state_name::Symbol = :Ũ⃗`: The name of the state variable.
  * `control_name::Symbol = :a`: The name of the control variable.
  * `timestep_name::Symbol = :Δt`: The name of the timestep variable.
  * `constraints::Vector{<:AbstractConstraint} = AbstractConstraint[]`: The constraints.
  * `a_bound::Float64 = 1.0`: The bound for the control amplitudes.
  * `a_bounds::Vector{Float64} = fill(a_bound, length(systems[1].G_drives))`: The bounds for the control amplitudes.
  * `a_guess::Union{Matrix{Float64}, Nothing} = nothing`: The initial guess for the control amplitudes.
  * `da_bound::Float64 = Inf`: The bound for the control first derivatives.
  * `da_bounds::Vector{Float64} = fill(da_bound, length(systems[1].G_drives))`: The bounds for the control first derivatives.
  * `dda_bound::Float64 = 1.0`: The bound for the control second derivatives.
  * `dda_bounds::Vector{Float64} = fill(dda_bound, length(systems[1].G_drives))`: The bounds for the control second derivatives.
  * `Δt_min::Float64 = 0.5 * Δt`: The minimum time step size.
  * `Δt_max::Float64 = 1.5 * Δt`: The maximum time step size.
  * `Q::Float64 = 100.0`: The fidelity weight.
  * `R::Float64 = 1e-2`: The regularization weight.
  * `R_a::Union{Float64, Vector{Float64}} = R`: The regularization weight for the control amplitudes.
  * `R_da::Union{Float64, Vector{Float64}} = R`: The regularization weight for the control first derivatives.
  * `R_dda::Union{Float64, Vector{Float64}} = R`: The regularization weight for the control second derivatives.
  * `piccolo_options::PiccoloOptions = PiccoloOptions()`: The Piccolo options.
