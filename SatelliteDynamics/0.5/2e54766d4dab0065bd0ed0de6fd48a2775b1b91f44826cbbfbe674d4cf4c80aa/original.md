Compute the rotation matrix from the Earth-fixed to the South-East-Zenith  coorindate basis.

Arguments:

  * `station_ecef::AbstractArray{<:Real, 1}`: Earth-fixed cartesian station coordinates
  * `conversion::Bool`: Conversion type to use. Can be "geocentric" or "geodetic"

Returns:

  * `E::AbstractArray{Float64, 2}`: Topocentric rotation matrix
