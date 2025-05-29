Computes the local atmospheric density using the NRLMSISE00 atmosphere model.

Arguments:

  * `epc::Epoch`: Epoch of computation. Used to lookup space weather data
  * `x::AbstractArray{<:Real, 1}`: Satellite state in geodetic coordinates [lon, lat, alt]
  * `use_degrees:Bool`: If `true` interprets geodetic inputs as being in degrees

Returns:

  * `rho:Float64`: Local atmospheric density [kg/m^3]

Notes:

1. Uses the gtd7d subroutine of the NRLMSISE00 to compute local atmospheric density. This subroutine includes the contribution of anomalous Oxygen in local density which is important for satellites above 500 km altitude.

References:

1. *Picone, JM, et al.* NRLMSISE-00 empirical model of the atmosphere: Statistical comparisons and scientific issues *Journal of Geophysical Research: Space Physics*
