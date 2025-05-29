```
linearize!(system, assembly; kwargs...)
```

Return the state variables, jacobian matrix, and mass matrix of a linearized system using the current system state vector.

# General Keyword Arguments

  * `prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}()`:      A dictionary with keys corresponding to the points at      which prescribed conditions are applied and values of type      [`PrescribedConditions`](@ref) which describe the prescribed conditions      at those points.  If time varying, this input may be provided as a      function of time.
  * `distributed_loads = Dict{Int,DistributedLoads{Float64}}()`: A dictionary      with keys corresponding to the elements to which distributed loads are      applied and values of type [`DistributedLoads`](@ref) which describe      the distributed loads on those elements.  If time varying, this input may      be provided as a function of time.
  * `point_masses = Dict{Int,PointMass{Float64}}()`: A dictionary with keys      corresponding to the points to which point masses are attached and values      of type [`PointMass`](@ref) which contain the properties of the attached      point masses.  If time varying, this input may be provided as a function of time.
  * `linear_velocity = zeros(3)`: Prescribed linear velocity of the body frame.      If time varying, this input may be provided as a function of time.
  * `angular_velocity = zeros(3)`: Prescribed angular velocity of the body frame.      If time varying, this input may be provided as a function of time.
  * `linear_acceleration = zeros(3)`: Prescribed linear acceleration of the body frame.      If time varying, this input may be provided as a function of time.
  * `angular_acceleration = zeros(3)`: Prescribed angular acceleration of the body frame.      If time varying, this input may be provided as a function of time.
  * `gravity = [0,0,0]`: Gravity vector in the inertial frame.  If time varying, this input      may be provided as a function of time.
  * `time = 0.0`: Current time or vector of times corresponding to each step. May be used      in conjunction with time varying prescribed conditions, distributed loads, and      body frame motion to gradually increase displacements and loads.

# Control Flag Keyword Arguments

  * `reset_state = true`: Flag indicating whether the system state variables should be       set to zero prior to performing this analysis.
  * `initial_state = nothing`: Object of type [`AssemblyState`](@ref) which contains the       initial state variables.  If not provided (or set to `nothing`), then the state       variables stored in `system` (which default to zeros) will be used as the initial       state variables.
  * `structural_damping = false`: Indicates whether to enable structural damping
  * `linear = false`: Flag indicating whether a linear analysis should be performed.
  * `two_dimensional = false`: Flag indicating whether to constrain results to the x-y plane
  * `show_trace = false`: Flag indicating whether to display the solution progress.

# Sensitivity Analysis Keyword Arguments

  * `xpfunc = (x, p, t) -> (;)`: Similar to `pfunc`, except that parameters can also be     defined as a function of GXBeam's state variables.  Using this function forces     the system jacobian to be computed using automatic differentiation and switches     the nonlinear solver to a Newton-Krylov solver (with linesearch).
  * `pfunc = (p, t) -> (;)`: Function which returns a named tuple with fields corresponding     to updated versions of the arguments `assembly`, `prescribed_conditions`,     `distributed_loads`, `point_masses`, `linear_velocity`, `angular_velocity`,     `linear_acceleration`, `angular_acceleration`, and `gravity`. Only fields contained     in the resulting named tuple will be overwritten.
  * `p`: Sensitivity parameters, as defined in conjunction with the keyword argument `pfunc`.     While not necessary, using `pfunc` and `p` to define the arguments to this function     allows automatic differentiation sensitivities to be computed more efficiently
