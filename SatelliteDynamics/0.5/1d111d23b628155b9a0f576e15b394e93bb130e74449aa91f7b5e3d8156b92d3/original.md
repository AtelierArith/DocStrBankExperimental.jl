Compute the satellite state at the given epoch as output from the SGP4 propagator.

Arguments:

  * `tle::TLE` Two-Line element object
  * `epc::Epoch` Epoch for SGP4 state
  * `opscode::Char` Operatitonal mode of propagators

Returns:

  * `rv::AbstractArray{Float64, 1}` Position and velocity as output by TLE propagator.    Units [m m/s]
