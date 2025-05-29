Compute the radial, along-track, cross-track (RTN) coordinates of a target satellite in the primary satellites RTN frame.

The RTN frame is also commonly refered to as the local-vertical, local-horizontal (LVLH) frame.

Arguments:

  * `x::AbstractVector{<:Real}`: Inertial state (position and velocity) of primary (observing) satellite
  * `xt::AbstractVector{<:Real}`: Inertial state (position and velocity) of the target satellite

Returns:

  * `xrtn::AbstractVector{<:Real}`: Position and velocity of the target relative of the observing satellite in the RTN.
