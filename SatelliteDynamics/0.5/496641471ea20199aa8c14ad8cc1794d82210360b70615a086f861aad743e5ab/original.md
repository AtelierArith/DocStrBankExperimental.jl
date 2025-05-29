Compute the coordinates of an object in the topocentric frame of an Earth-fixed frame

Arguments:

  * `station_ecef::AbstractArray{<:Real, 1}`: Earth-fixed cartesian station coordinates
  * `sez::AbstractArray{<:Real, 1}`: SEZ coordinates of the object
  * `conversion::Bool`: Conversion type to use. Can be "geocentric" or "geodetic"

Returns:

  * `E::AbstractArray{Float64, 2}`: Topocentric rotation matrix
