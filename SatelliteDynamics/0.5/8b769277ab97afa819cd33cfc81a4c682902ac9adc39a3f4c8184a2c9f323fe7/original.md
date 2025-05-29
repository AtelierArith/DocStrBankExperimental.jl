Convert eccentric anomaly into mean anomaly.

Arguments:

  * `E::Real`: Eccentric anomaly. [rad] or [deg]
  * `e::Real`: Eccentricity. [dimensionless]
  * `use_degrees:Bool`: If `true` interpret input will be interpreted as being in degrees, and output will be returned in degrees.

Returns:

  * `M::Real`: Mean anomaly. [rad] or [deg]
