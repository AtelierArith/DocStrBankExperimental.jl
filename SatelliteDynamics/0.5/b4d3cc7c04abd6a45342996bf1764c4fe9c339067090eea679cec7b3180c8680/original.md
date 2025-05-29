Computes perturbation accleration of a satellite in the Inertial frame due to the combined effects of special and general relativity.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: Satellite Cartesean state in the inertial reference frame [m; m/s]

Returns:

  * `a::AbstractArray{<:Real, 1}`: Satellite acceleration due to relativity. [m/s^2]

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.110-112.
