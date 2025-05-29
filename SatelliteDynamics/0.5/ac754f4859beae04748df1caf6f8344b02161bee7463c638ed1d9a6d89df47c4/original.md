Compute the required inclination for a Sun-synchronous Earth orbit.

Algorithm assumes the nodal precession is entirely due to the J2 perturbation, and no other perturbations are considered.

The inclination is computed using a first-order, non-iterative approximation.

Arguments:

  * `a::Real`: Semi-major axis. [m]
  * `e::Real`: Eccentricity. [dimensionless]
  * `use_degrees:Bool`: If `true` interpret output will be returned in degrees.

Returns:

  * `iss::Real`: Requierd inclination for a sun-synchronous orbit. [rad] or [deg]
