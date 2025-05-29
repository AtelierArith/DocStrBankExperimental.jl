Compute the satellite state in the Earth-centered inertial.

Arguments:

  * `tle::TLE` Two-Line element object
  * `epc::Epoch` Epoch for SGP4 state

Returns:

  * `eci::AbstractArray{Float64, 1}` Position and velocity in ECI frame. Units [m; m/s]
