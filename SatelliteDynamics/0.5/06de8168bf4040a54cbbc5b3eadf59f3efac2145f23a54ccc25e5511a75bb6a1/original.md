Arguments:

  * `x::AbstractVector{<:Real}`: Inertial state (position and velocity) of primary (observing) satellite
  * `xrtn::SVector{6,<:Real}`: Inertial state (position and velocity) of the target satellite

Returns:

  * `xt::SVector{6,<:Real}`: Position and velocity of the target relative of the observing satellite in the RTN.
