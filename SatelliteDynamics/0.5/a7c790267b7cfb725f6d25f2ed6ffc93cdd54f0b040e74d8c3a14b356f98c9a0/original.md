Compute the mean motion given a semi-major axis.

Arguments:

  * `a::Real`: Semi-major axis. [m]
  * `use_degrees:Bool`: If `true` returns result in units of degrees
  * `GM::Real`: Gravitational constant of central body. Defaults to `SatelliteDynamics.GM_EARTH` if none is provided.

Returns:

  * `n::Real`: Orbital mean motion. [rad/s] or [deg/s]
