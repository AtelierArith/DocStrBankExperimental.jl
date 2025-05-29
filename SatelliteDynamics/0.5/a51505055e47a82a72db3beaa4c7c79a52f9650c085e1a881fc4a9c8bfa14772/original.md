Computes the Earth rotation matrix transforming the TIRS to the ITRF reference  frame.

# Arguments

  * `epc::Epoch`: Epoch of transformation

# Returns

  * `rpm::Matrix{<:Real}`: 3x3 Rotation matrix transforming TIRS -> ITRF
