Satellite orbit state vector using an Earth inertial state representation and dynamics model.

If an initial state transition matrix is provided it will be used for propagation if there is no state transition matrix then only the state will be propagated.

Attributes:

  * `rk4::RK4` Internal numerical integrator used for state propagation
  * `dt::Real` Default propagation time step. All steps will be this size unless

the state vector is requested to propagate to a time smaller than this step size, which it will do.

  * `epc::Epoch` Epoch of state
  * `x::AbstractArray{Float64, 1}` State vector. Earth-centered inertial Cartesian state.
  * `phi::Union{Nothing, Array{Float64, 2}}` State transition matrix, or the matrix

of partial derivatives of the state at the current time with respect to the  start of propagation.

The following force model parametters can be set as keyword arguments

Parameters:

  * `mass::Real`: Satellite mass [kg]
  * `area_drag`: Velocity-facing area affected by drag. [m^2]
  * `coef_drag`: Coefficient of drag [dimensionless]
  * `area_srp`: Velocity-facing area affected by drag. [m^2]
  * `coef_srp`: Coefficient of reflectivity [dimensionless]
  * `n_grav::Integer`: Gravity model degree (Default: 20)
  * `m_grav::Integer`: Gravity model order (Default: 20)
  * `drag::Bool`: Include cannonball atomospheric drag in force model (Default: `true`)
  * `srp::Bool`: Include flat-plate solar radiation pressure in force model (Default: `true`)
  * `moon::Bool`: Include thridbody lunar gravity in force model (Default: `true`)
  * `sun::Bool`: Include thirdbody solar in force model (Default: `true`)
  * `relativity::Bool`: Include relativistic effects in force model (Default: `true`)
