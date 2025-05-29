Convert mean anomaly into eccentric anomaly.

Arguments:

  * `M::Real`: Mean anomaly. [deg] or [deg]
  * `e::Real`: Eccentricity. [dimensionless]
  * `use_degrees:Bool`: If `true` interpret input will be interpreted as being in degrees, and output will be returned in degrees.

Returns:

  * `E::Real`: Eccentric anomaly. [rad] or [deg]
