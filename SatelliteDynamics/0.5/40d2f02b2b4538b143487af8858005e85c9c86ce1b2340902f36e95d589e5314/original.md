Arguments:

  * `x::AbstractVector{<:Real}`: Inertial state (position and velocity) of primary (observing) satellite
  * `xt::SVector{3,<:Real}`: Inertial state (position) of the target satellite

Returns:

  * `xrtn::SVector{3,<:Real}`: Position of the target relative of the observing satellite in the RTN.
