Convert geodetic coordinaties to Earth-fixed position

Arguments:

  * `ecef::AbstractArray{<:Real, 1}`: Earth-fixed position [m]
  * `use_degrees:Bool`: If `true` returns result in units of degrees

Returns:

  * `geod::AbstractArray{<:Real, 1}`: Geocentric coordinates (lon, lat, altitude) [rad] / [deg]
