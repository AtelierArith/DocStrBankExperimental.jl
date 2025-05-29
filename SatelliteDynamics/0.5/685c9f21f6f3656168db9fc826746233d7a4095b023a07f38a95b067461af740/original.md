Compute the Earth-center

The RTN frame is also commonly refered to as the local-vertical, local-horizontal (LVLH) frame.

Arguments:

  * `x::AbstractVector{<:Real}`: Inertial state (position and velocity) of primary (observing) satellite
  * `xrtn::AbstractVector{<:Real}`: Inertial state (position and velocity) of the target satellite

Returns:

  * `xt::AbstractVector{<:Real}`: Position and velocity of the target relative of the observing satellite in the RTN.
