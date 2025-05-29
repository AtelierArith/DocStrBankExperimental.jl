Transforms an Earth inertial state into an Earth fixed state

The transformation is accomplished using the IAU 2006/2000A, CIO-based  theory using classical angles. The method as described in section 5.5 of  the SOFA C transformation cookbook.

# Arguments

  * `epc::Epoch`: Epoch of transformation
  * `x::AbstractVector{<:Real}`: Inertial state (position, velocity) [m; m/s]

# Returns

  * `x_ecef::Vector{<:Real}`: Earth-fixed state (position, velocity)
