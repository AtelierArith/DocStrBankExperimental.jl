Compute the rotation matrix from the Earth-fixed to the East-North-Up coorindate basis.

Arguments:

  * `station_ecef::AbstractArray{<:Real, 1}`: Earth-fixed cartesian station coordinates
  * `conversion::Bool`: Conversion type to use. Can be "geocentric" or "geodetic"

Returns:

  * `E::AbstractArray{Real, 2}`: Topocentric rotation matrix
