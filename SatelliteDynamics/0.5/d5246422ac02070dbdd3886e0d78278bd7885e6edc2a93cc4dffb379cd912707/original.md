Computes the Bias-Precession-Nutation matrix transforming the GCRS to the  CIRS intermediate reference frame. This transformation corrects for the  bias, precession, and nutation of Celestial Intermediate Origin (CIO) with respect to inertial space.

Arguments:

  * `epc::Epoch`: Epoch of transformation

Returns:

  * `rc2i::Matrix{<:Real}`: 3x3 Rotation matrix transforming GCRS -> CIRS
