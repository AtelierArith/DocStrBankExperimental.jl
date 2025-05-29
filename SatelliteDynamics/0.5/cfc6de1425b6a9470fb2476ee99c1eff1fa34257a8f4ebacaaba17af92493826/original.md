Computes the illumination fraction of a satellite in Earth orbit using a conical Earth shadow model.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: Satellite Cartesean state in the inertial reference frame [m; m/s]
  * `r_sun::AbstractArray{<:Real, 1}`: Position of sun in inertial frame.

Return:

  * `nu::Float64`: Illumination fraction (0 <= nu <= 1). nu = 0 means spacecraft in complete shadow, nu = 1 mean spacecraft fully illuminated by sun.

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.80-83.
