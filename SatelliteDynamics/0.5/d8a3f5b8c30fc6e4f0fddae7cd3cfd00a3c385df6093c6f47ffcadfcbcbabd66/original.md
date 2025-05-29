Compute the radial, along-track, cross-track (RTN) to Earth-centered inertial rotation matrix. If applied to a position vector in the RTN frame, it will transform that vector to into the equivalent position vector in the ECI frame.

The RTN frame is also commonly refered to as the local-vertical, local-horizontal (LVLH) frame.

Arguments:

  * `x::AbstractVector{<:Real}`: Inertial state (position and velocity) of primary (observing) satellite

Returns:

  * `R_rtn2eci::SMatrix{3,3}`: Rotation matrix transforming *from* the RTN frame *to* the ECI frame
