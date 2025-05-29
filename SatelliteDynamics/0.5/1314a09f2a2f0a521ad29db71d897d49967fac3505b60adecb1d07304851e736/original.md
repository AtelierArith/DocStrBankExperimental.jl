Transforms an Earth fixed state into an Inertial state

The transformation is accomplished using the IAU 2006/2000A, CIO-based  theory using classical angles. The method as described in section 5.5 of  the SOFA C transformation cookbook.

# Arguments

  * `epc::Epoch`: Epoch of transformation
  * `x::AbstractVector{<:Real}`: Earth-fixed state (position, velocity) [m; m/s]

# Returns

  * `x_eci::Vector{<:Real}`: Inertial state (position, velocity)
