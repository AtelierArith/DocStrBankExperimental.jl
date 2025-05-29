Convert Earth-fixed position to geocentric location.

Arguments:

  * `ecef::AbstractArray{<:Real, 1}`: Earth-fixed coordinated [m]
  * `use_degrees:Bool`: If `true` returns result in units of degrees

Returns:

  * `geoc`: Geocentric coordinates (lon, lat, altitude) [rad] / [deg]
