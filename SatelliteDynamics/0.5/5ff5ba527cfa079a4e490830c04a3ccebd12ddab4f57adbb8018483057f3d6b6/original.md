Compute the state derivative.

Arguments:

  * `epc::Epoch`: Current epoch
  * `x::AbstractArray{<:Real, 1}`: Satellite state vector
  * `mass::Real`: Satellite mass [kg]
  * `area_drag`: Velocity-facing area affected by drag. [m^2]
  * `coef_drag`: Coefficient of drag [dimensionless]
  * `area_srp`: Sun-facing area affected by solar-radiation pressure. [m^2]
  * `coef_srp`: Coefficient of reflectivity [dimensionless]
  * `n_grav::Integer`: Gravity model degree (Default: 20)
  * `m_grav::Integer`: Gravity model order (Default: 20)
  * `drag::Bool`: Include cannonball atomospheric drag in force model (Default: `true`)
  * `srp::Bool`: Include flat-plate solar radiation pressure in force model (Default: `true`)
  * `moon::Bool`: Include thridbody lunar gravity in force model (Default: `true`)
  * `sun::Bool`: Include thirdbody solar in force model (Default: `true`)
  * `relativity::Bool`: Include relativistic effects in force model (Default: `true`)

Returns:

  * `dx::AbstractArray{<:Float64, 1}`: Satellite state derivative, velocity and accelerations [m; m/s]
