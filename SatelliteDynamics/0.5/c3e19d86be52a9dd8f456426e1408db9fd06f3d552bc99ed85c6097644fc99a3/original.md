Compute the coordinates of an object in the topocentric frame of an Earth-fixed frame

Arguments:

  * `station_ecef::AbstractArray{<:Real, 1}`: Earth-fixed cartesian station coordinates
  * `ecef::AbstractArray{<:Real, 1}`: Coordinates of the object in Earth-fixed station
  * `conversion::Bool`: Conversion type to use. Can be "geocentric" or "geodetic"

Returns:

  * `E::AbstractArray{Float64, 2}`: Topocentric rotation matrix
