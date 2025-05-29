```
initial_condition_analysis(assembly, t0; kwargs...)
```

Perform an analysis to obtain a consistent set of initial conditions.  Return the resulting system and a flag indicating whether the iteration procedure converged.

# General Keyword Arguments

  * `prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}()`:      A dictionary with keys corresponding to the points at      which prescribed conditions are applied and values of type      [`PrescribedConditions`](@ref) which describe the prescribed conditions      at those points.  If time varying, this input may be provided as a      function of time.
  * `distributed_loads = Dict{Int,DistributedLoads{Float64}}()`: A dictionary      with keys corresponding to the elements to which distributed loads are      applied and values of type [`DistributedLoads`](@ref) which describe      the distributed loads on those elements.  If time varying, this input may      be provided as a function of time.
  * `point_masses = Dict{Int,PointMass{Float64}}()`: A dictionary with keys      corresponding to the points to which point masses are attached and values      of type [`PointMass`](@ref) which contain the properties of the attached      point masses.  If time varying, this input may be provided as a function of time.
  * `linear_velocity = zeros(3)`: Initial linear velocity of the body frame.
  * `angular_velocity = zeros(3)`: Initial angular velocity of the body frame.
  * `linear_acceleration = zeros(3)`: Initial linear acceleration of the body frame.
  * `angular_acceleration = zeros(3)`: Initial angular acceleration of the body frame.
  * `gravity = [0,0,0]`: Gravity vector in the inertial frame.

# Control Flag Keyword Arguments

  * `reset_state = true`: Flag indicating whether the system state variables should be      set to zero prior to performing this analysis.
  * `initial_state = nothing`: Object of type [`AssemblyState`](@ref) which contains the      initial state variables.  If not provided (or set to `nothing`), then the state      variables stored in `system` (which default to zeros) will be used as the initial      state variables.
  * `structural_damping = true`: Indicates whether to enable structural damping
  * `linear = false`: Flag indicating whether a linear analysis should be performed.
  * `two_dimensional = false`: Flag indicating whether to constrain results to the x-y plane
  * `steady_state=false`: Flag indicating whether to initialize by performing a steady state      analysis.
  * `show_trace = false`: Flag indicating whether to display the solution progress.

# Initial Condition Analysis Keyword Arguments

  * `u0 = fill(zeros(3), length(assembly.points))`: Initial linear displacement of      each point **relative to the body frame**
  * `theta0 = fill(zeros(3), length(assembly.points))`: Initial angular displacement of      each point **relative to the body frame** (using Wiener-Milenkovic Parameters)
  * `V0 = fill(zeros(3), length(assembly.points))`: Initial linear velocity of      each point **relative to the body frame**
  * `Omega0 = fill(zeros(3), length(assembly.points))`: Initial angular velocity of      each point **relative to the body frame**
  * `Vdot0 = fill(zeros(3), length(assembly.points))`: Initial linear acceleration of      each point **relative to the body frame**
  * `Omegadot0 = fill(zeros(3), length(assembly.points))`: Initial angular acceleration of      each point **relative to the body frame**

# Linear Analysis Keyword Arguments

  * `update_linearization = false`: Flag indicating whether to update the linearization state      variables for a linear analysis with the instantaneous state variables. If `false`,      then the initial set of state variables will be used for the linearization.

# Nonlinear Analysis Keyword Arguments

  * `method = :newton`: Method (as defined in NLsolve) to solve nonlinear system of equations
  * `linesearch = LineSearches.BackTracking(maxstep=1e6)`: Line search used to solve the      nonlinear system of equations
  * `ftol = 1e-9`: tolerance for solving the nonlinear system of equations
  * `iterations = 1000`: maximum iterations for solving the nonlinear system of equations

# Sensitivity Analysis Keyword Arguments

  * `xpfunc = (x, p, t) -> (;)`: Similar to `pfunc`, except that parameters can also be      defined as a function of GXBeam's state variables.  Using this function forces      the system jacobian to be computed using automatic differentiation and switches      the nonlinear solver to a Newton-Krylov solver (with linesearch).
  * `pfunc = (p, t) -> (;)`: Function which returns a named tuple with fields corresponding      to updated versions of the arguments `assembly`, `prescribed_conditions`,      `distributed_loads`, `point_masses`, `linear_velocity`, `angular_velocity`,      `linear_acceleration`, `angular_acceleration`, `gravity`, `u0`, `theta0`, `V0`,      `Omega0`, `Vdot0`, and `Omegadot0`. Only fields contained in the resulting named      tuple will be overwritten.
  * `p`: Sensitivity parameters, as defined in conjunction with the keyword argument `pfunc`.      While not necessary, using `pfunc` and `p` to define the arguments to this function      allows automatic differentiation sensitivities to be computed more efficiently
