Calculate semi-major axis given mean-motion.

Arguments:

  * `n::Real`: Orbital mean motion. [rad/s] or [deg/s]
  * `use_degrees:Bool`: If `true` interpret input as being in degrees.
  * `GM::Real`: Gravitational constant of central body. Defaults to `SatelliteDynamics.GM_EARTH` if none is provided.

Returns:

  * `a::Real`: Semi-major axis. [m]
