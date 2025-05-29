```
UnitarySmoothPulseProblem(system::AbstractQuantumSystem, operator, T, Δt; kwargs...)
UnitarySmoothPulseProblem(H_drift, H_drives, operator, T, Δt; kwargs...)
```

Construct a `DirectTrajOptProblem` for a free-time unitary gate problem with smooth control pulses enforced by constraining the second derivative of the pulse trajectory, i.e.,

$$
\begin{aligned}
\underset{\vec{\tilde{U}}, a, \dot{a}, \ddot{a}, \Delta t}{\text{minimize}} & \quad
Q \cdot \ell\qty(\vec{\tilde{U}}_T, \vec{\tilde{U}}_{\text{goal}}) + \frac{1}{2} \sum_t \qty(R_a a_t^2 + R_{\dot{a}} \dot{a}_t^2 + R_{\ddot{a}} \ddot{a}_t^2) \\
\text{ subject to } & \quad \vb{P}^{(n)}\qty(\vec{\tilde{U}}_{t+1}, \vec{\tilde{U}}_t, a_t, \Delta t_t) = 0 \\
& \quad a_{t+1} - a_t - \dot{a}_t \Delta t_t = 0 \\
& \quad \dot{a}_{t+1} - \dot{a}_t - \ddot{a}_t \Delta t_t = 0 \\
& \quad |a_t| \leq a_{\text{bound}} \\
& \quad |\ddot{a}_t| \leq \ddot{a}_{\text{bound}} \\
& \quad \Delta t_{\text{min}} \leq \Delta t_t \leq \Delta t_{\text{max}} \\
\end{aligned}
$$

where, for $U \in SU(N)$,

$$
\ell\qty(\vec{\tilde{U}}_T, \vec{\tilde{U}}_{\text{goal}}) =
\abs{1 - \frac{1}{N} \abs{ \tr \qty(U_{\text{goal}}, U_T)} }
$$

is the *infidelity* objective function, $Q$ is a weight, $R_a$, $R_{\dot{a}}$, and $R_{\ddot{a}}$ are weights on the regularization terms, and $\vb{P}^{(n)}$ is the $n$th-order Pade integrator.

# Arguments

  * `system::AbstractQuantumSystem`: the system to be controlled

or

  * `H_drift::AbstractMatrix{<:Number}`: the drift hamiltonian
  * `H_drives::Vector{<:AbstractMatrix{<:Number}}`: the control hamiltonians

with

  * `goal::AbstractPiccoloOperator`: the target unitary, either in the form of an `EmbeddedOperator` or a `Matrix{ComplexF64}
  * `T::Int`: the number of timesteps
  * `Δt::Float64`: the (initial) time step size

# Keyword Arguments

  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: the options for the Piccolo solver
  * `state_name::Symbol = :Ũ⃗`: the name of the state
  * `control_name::Symbol = :a`: the name of the control
  * `timestep_name::Symbol = :Δt`: the name of the timestep
  * `init_trajectory::Union{NamedTrajectory, Nothing}=nothing`: an initial trajectory to use
  * `a_guess::Union{Matrix{Float64}, Nothing}=nothing`: an initial guess for the control pulses
  * `a_bound::Float64=1.0`: the bound on the control pulse
  * `a_bounds::Vector{Float64}=fill(a_bound, length(system.G_drives))`: the bounds on the control pulses, one for each drive
  * `da_bound::Float64=Inf`: the bound on the control pulse derivative
  * `da_bounds::Vector{Float64}=fill(da_bound, length(system.G_drives))`: the bounds on the control pulse derivatives, one for each drive
  * `dda_bound::Float64=1.0`: the bound on the control pulse second derivative
  * `dda_bounds::Vector{Float64}=fill(dda_bound, length(system.G_drives))`: the bounds on the control pulse second derivatives, one for each drive
  * `Δt_min::Float64=Δt isa Float64 ? 0.5 * Δt : 0.5 * mean(Δt)`: the minimum time step size
  * `Δt_max::Float64=Δt isa Float64 ? 1.5 * Δt : 1.5 * mean(Δt)`: the maximum time step size
  * `Q::Float64=100.0`: the weight on the infidelity objective
  * `R=1e-2`: the weight on the regularization terms
  * `R_a::Union{Float64, Vector{Float64}}=R`: the weight on the regularization term for the control pulses
  * `R_da::Union{Float64, Vector{Float64}}=R`: the weight on the regularization term for the control pulse derivatives
  * `R_dda::Union{Float64, Vector{Float64}}=R`: the weight on the regularization term for the control pulse second derivatives
  * `constraints::Vector{<:AbstractConstraint}=AbstractConstraint[]`: the constraints to enforce
