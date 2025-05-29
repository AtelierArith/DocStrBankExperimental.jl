Computes the perturbing acceleration due to direct solar radiation  pressure assuming the reflecting surface is a flat plate pointed directly at the Sun.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: Satellite Cartesean state in the inertial reference frame [m; m/s]

Returns:

  * `a::AbstractArray{<:Real, 1}`: Satellite acceleration due to solar radiation pressure [m/s^2]

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.77-79.
