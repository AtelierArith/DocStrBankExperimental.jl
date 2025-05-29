Computes the acceleration of a satellite caused by a point-mass approximation  of the central body. Returns the acceleration vector of the satellite.

Assumes the satellite is much, much less massive than the central body.

Arguments:

  * `r_sat::AbstractArray{<:Real, 1}`: satellite position in a commonn inertial frame [m]
  * `r_body::AbstractArray{<:Real, 1}`: position of body in a commonn inertial frame [m]
  * `GM::AbstractArray{<:Real, 1}`: gravitational coeffient of attracting body [m^3/s^2] Default: SatelliteDynamics.GM_EARTH)

(Default: SatelliteDynamics.GM_EARTH

Return:

  * `a::AbstractArray{<:Real, 1}`: Acceleration in X, Y, and Z inertial directions [m/s^2]
