```
time_domain_analysis(assembly, tvec; kwargs...)
```

Perform a time-domain analysis for the system of nonlinear beams contained in `assembly` using the time vector `tvec`.  Return the final system, a post-processed solution history, and a convergence flag indicating whether the iteration procedure converged for every time step.

# General Keyword Arguments

  * `prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}()`:      A dictionary with keys corresponding to the points at      which prescribed conditions are applied and values of type      [`PrescribedConditions`](@ref) which describe the prescribed conditions      at those points.  If time varying, this input may be provided as a      function of time.
  * `distributed_loads = Dict{Int,DistributedLoads{Float64}}()`: A dictionary      with keys corresponding to the elements to which distributed loads are      applied and values of type [`DistributedLoads`](@ref) which describe      the distributed loads on those elements.  If time varying, this input may      be provided as a function of time.
  * `point_masses = Dict{Int,PointMass{Float64}}()`: A dictionary with keys      corresponding to the points to which point masses are attached and values      of type [`PointMass`](@ref) which contain the properties of the attached      point masses.  If time varying, this input may be provided as a function of time.
  * `linear_velocity = zeros(3)`: Prescribed linear velocity of the body frame.
  * `angular_velocity = zeros(3)`: Prescribed angular velocity of the body frame.
  * `linear_acceleration = zeros(3)`: Initial linear acceleration of the body frame.
  * `angular_acceleration = zeros(3)`: Initial angular acceleration of the body frame.
  * `gravity = [0,0,0]`: Gravity vector in the body frame.  If time varying, this input      may be provided as a function of time.

# Control Flag Keyword Arguments

  * `reset_state = true`: Flag indicating whether the system state variables should be      set to zero prior to performing this analysis.
  * `initial_state = nothing`: Object of type `AssemblyState`, which defines the initial      states and state rates corresponding to the analysis.  By default, this input is      calculated using either `steady_state_analysis` or `initial_condition_analysis`.
  * `steady_state = false`: Flag indicating whether to compute the state variables      corresponding to the keyword argument `initial_state` using `steady_state_analysis`      (rather than `initial_condition_analysis`).
  * `structural_damping = true`: Flag indicating whether to enable structural damping
  * `linear = false`: Flag indicating whether a linear analysis should be performed.
  * `two_dimensional = false`: Flag indicating whether to constrain results to the x-y plane
  * `show_trace = false`: Flag indicating whether to display the solution progress.
  * `save = eachindex(tvec)`: Steps at which to save the time history

# Initial Condition Analysis Arguments

  * `u0 = fill(zeros(3), length(assembly.points))`: Initial linear displacement of      each point in the body frame
  * `theta0 = fill(zeros(3), length(assembly.points))`: Initial angular displacement of      each point in the body frame (using Wiener-Milenkovic Parameters)
  * `V0 = fill(zeros(3), length(assembly.points))`: Initial linear velocity of      each point in the body frame **excluding contributions from body frame motion**
  * `Omega0 = fill(zeros(3), length(assembly.points))`: Initial angular velocity of      each point in the body frame **excluding contributions from body frame motion**
  * `Vdot0 = fill(zeros(3), length(assembly.points))`: Initial linear acceleration of      each point in the body frame **excluding contributions from body frame motion**
  * `Omegadot0 = fill(zeros(3), length(assembly.points))`: Initial angular acceleration of      each point in the body frame **excluding contributions from body frame motion**

# Linear Analysis Keyword Arguments

  * `update_linearization = false`: Flag indicating whether to update the linearization state      variables for a linear analysis with the instantaneous state variables. If `false`,      then the initial set of state variables will be used for the linearization.

# Nonlinear Analysis Keyword Arguments

  * `method = :newton`: Method (as defined in NLsolve) to solve nonlinear system of equations
  * `linesearch = LineSearches.BackTracking(maxstep=1e6)`: Line search used to solve      nonlinear systems of equations
  * `ftol = 1e-9`: tolerance for solving the nonlinear system of equations
  * `iterations = 1000`: maximum iterations for solving the nonlinear system of equations

# Sensitivity Analysis Keyword Arguments

  * `xpfunc = (x, p, t) -> (;)`: Similar to `pfunc`, except that parameters can also be      defined as a function of GXBeam's state variables.  Using this function forces      the system jacobian to be computed using automatic differentiation and switches      the nonlinear solver to a Newton-Krylov solver (with linesearch).
  * `pfunc = (p, t) -> (;)`: Function which returns a named tuple with fields corresponding      to updated versions of the arguments `assembly`, `prescribed_conditions`,      `distributed_loads`, `point_masses`, `linear_velocity`, `angular_velocity`,      `linear_acceleration`, `angular_acceleration`, `gravity`, `u0`, `theta0`, `V0`,      `Omega0`, `Vdot0`, and `Omegadot0`. Only fields contained in the resulting named      tuple will be overwritten.
  * `p`: Sensitivity parameters, as defined in conjunction with the keyword argument `pfunc`.      While not necessary, using `pfunc` and `p` to define the arguments to this function      allows automatic differentiation sensitivities to be computed more efficiently
