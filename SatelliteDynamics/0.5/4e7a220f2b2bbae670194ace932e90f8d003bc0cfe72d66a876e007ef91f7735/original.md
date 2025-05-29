Computes the acceleration of a satellite in the inertial frame due to the gravitational attraction of the Sun.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: Satellite Cartesean state in the inertial reference frame [m; m/s]
  * `r_sun::AbstractArray{<:Real, 1}`: Position of sun in inertial frame.

Return:

  * `a::AbstractArray{<:Real, 1}`: Acceleration due to the Sun's gravity in the inertial frame [m/s^2]

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.69-70.
