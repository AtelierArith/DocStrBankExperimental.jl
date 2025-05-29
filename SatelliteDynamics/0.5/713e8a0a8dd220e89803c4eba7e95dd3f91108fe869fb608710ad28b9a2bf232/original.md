Computes the Earth rotation matrix transforming the CIRS to the TIRS intermediate reference frame. This transformation corrects for the Earth rotation.

Arguments:

  * `epc::Epoch`: Epoch of transformation

Returns:

  * `r::Matrix{<:Real}`: 3x3 Rotation matrix transforming CIRS -> TIRS
