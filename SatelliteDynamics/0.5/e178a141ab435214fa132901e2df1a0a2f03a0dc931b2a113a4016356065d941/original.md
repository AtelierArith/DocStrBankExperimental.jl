Convert geocentric position to equivalent Earth-fixed position.

Arguments:

  * `geoc::AbstractArray{<:Real, 1}`: Geocentric coordinates (lon, lat, altitude) [rad] / [deg]
  * `use_degrees:Bool`: If `true` interpret input as being in degrees.

Returns:

  * `ecef::AbstractArray{<:Real, 1}`: Earth-fixed coordinates [m]
