```
QuantumStateSmoothPulseProblem(system, ψ_inits, ψ_goals, T, Δt; kwargs...)
QuantumStateSmoothPulseProblem(system, ψ_init, ψ_goal, T, Δt; kwargs...)
QuantumStateSmoothPulseProblem(H_drift, H_drives, args...; kwargs...)
```

Create a quantum state smooth pulse problem. The goal is to find a control pulse `a(t)`  that drives all of the initial states `ψ_inits` to the corresponding target states  `ψ_goals` using `T` timesteps of size `Δt`. This problem also controls the  first and  second derivatives of the control pulse, `da(t)` and `dda(t)`, to ensure smoothness.

# Arguments

  * `system::AbstractQuantumSystem`: The quantum system.

or

  * `H_drift::AbstractMatrix{<:Number}`: The drift Hamiltonian.
  * `H_drives::Vector{<:AbstractMatrix{<:Number}}`: The control Hamiltonians.

with

  * `ψ_inits::Vector{<:AbstractVector{<:ComplexF64}}`: The initial states.
  * `ψ_goals::Vector{<:AbstractVector{<:ComplexF64}}`: The target states.

or

  * `ψ_init::AbstractVector{<:ComplexF64}`: The initial state.
  * `ψ_goal::AbstractVector{<:ComplexF64}`: The target state.

with

  * `T::Int`: The number of timesteps.
  * `Δt::Float64`: The timestep size.

# Keyword Arguments

  * `state_name::Symbol=:ψ̃`: The name of the state variable.
  * `control_name::Symbol=:a`: The name of the control variable.
  * `timestep_name::Symbol=:Δt`: The name of the timestep variable.
  * `init_trajectory::Union{NamedTrajectory, Nothing}=nothing`: The initial trajectory.
  * `a_bound::Float64=1.0`: The bound on the control pulse.
  * `a_bounds::Vector{Float64}=fill(a_bound, length(system.G_drives))`: The bounds on the control pulse.
  * `a_guess::Union{Matrix{Float64}, Nothing}=nothing`: The initial guess for the control pulse.
  * `da_bound::Float64=Inf`: The bound on the first derivative of the control pulse.
  * `da_bounds::Vector{Float64}=fill(da_bound, length(system.G_drives))`: The bounds on the first derivative of the control pulse.
  * `dda_bound::Float64=1.0`: The bound on the second derivative of the control pulse.
  * `dda_bounds::Vector{Float64}=fill(dda_bound, length(system.G_drives))`: The bounds on the second derivative of the control pulse.
  * `Δt_min::Float64=0.5 * Δt`: The minimum timestep size.
  * `Δt_max::Float64=1.5 * Δt`: The maximum timestep size.
  * `drive_derivative_σ::Float64=0.01`: The standard deviation of the drive derivative random initialization.
  * `Q::Float64=100.0`: The weight on the state objective.
  * `R=1e-2`: The weight on the control pulse and its derivatives.
  * `R_a::Union{Float64, Vector{Float64}}=R`: The weight on the control pulse.
  * `R_da::Union{Float64, Vector{Float64}}=R`: The weight on the first derivative of the control pulse.
  * `R_dda::Union{Float64, Vector{Float64}}=R`: The weight on the second derivative of the control pulse.
  * `constraints::Vector{<:AbstractConstraint}=AbstractConstraint[]`: The constraints.
  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: The Piccolo options.
