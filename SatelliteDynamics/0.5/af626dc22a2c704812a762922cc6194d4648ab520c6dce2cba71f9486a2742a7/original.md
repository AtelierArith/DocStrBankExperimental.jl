Compute the satellite orbital period given the semi-major axis.

Arguments:

  * `a::Real`: Semi-major axis. [m]
  * `GM::Real`: Gravitational constant of central body. Defaults to `SatelliteDynamics.GM_EARTH` if none is provided.

Returns:

  * `T::Real`: Orbital period. [s]
