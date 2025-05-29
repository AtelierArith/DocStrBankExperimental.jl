Convert geodetic position to equivalent Earth-fixed position.

Arguments:

  * `geod::AbstractArray{<:Real, 1}`: Geodetic coordinates (lon, lat, altitude) [rad] / [deg]
  * `use_degrees:Bool`: If `true` interpret input as being in degrees.

Returns:

  * `ecef::AbstractArray{<:Real, 1}`: Earth-fixed coordinates [m]
