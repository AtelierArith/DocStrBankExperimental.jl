Computes the combined rotation matrix from the Earth-fixed to the inertial reference frame. Applies corrections for bias, precession, nutation, Earth-rotation, and polar motion.

The transformation is accomplished using the IAU 2006/2000A, CIO-based  theory using classical angles. The method as described in section 5.5 of  the SOFA C transformation cookbook.

# Arguments

  * `epc::Epoch`: Epoch of transformation

# Returns

  * `r::Matrix{<:Real}`: 3x3 Rotation matrix transforming ITRF -> GCRF
