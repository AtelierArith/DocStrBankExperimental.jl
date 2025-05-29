Compute the satellite state in the Earth-fixed frame.

Arguments:

  * `tle::TLE` Two-Line element object
  * `epc::Epoch` Epoch for SGP4 state

Returns:

  * `ecef::AbstractArray{Float64, 1}` Position and velocity in ECEF frame. Units [m; m/s]
