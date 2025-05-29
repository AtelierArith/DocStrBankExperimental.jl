Compute the Earth-centered inertial to radial, along-track, cross-track (RTN) rotation matrix. If applied to a position vector in the ECI frame, it will transform that vector into the equivalent position vector in the RTN frame.

The RTN frame is also commonly refered to as the local-vertical, local-horizontal (LVLH) frame.

Arguments:

  * `x::AbstractVector{<:Real}`: Inertial state (position and velocity) of primary (observing) satellite

Returns:

  * `R_eci2rtn::SMatrix{3,3}`: Rotation matrix transforming *from* the ECI frame *to* the RTN frame
