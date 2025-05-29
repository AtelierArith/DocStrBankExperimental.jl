Computes the local density using the Harris-Priester density model.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: Satellite Cartesean state in the inertial reference frame [m; m/s]
  * `r_sun::AbstractArray{<:Real, 1}`: Position of sun in inertial frame.

Returns:

  * `rho:Float64`: Local atmospheric density [kg/m^3]

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.89-91.
