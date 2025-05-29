Computes the acceleration on a satellite caused by a point-mass approximation  of a massive body. Returns the acceleration vector of the satellite.

Arguments:

  * `r_sat::AbstractArray{<:Real, 1}`: satellite position in the inertial frame [m]
  * `GM::AbstractArray{<:Real, 1}`: gravitational coeffient of attracting body [m^3/s^2] Default: SatelliteDynamics.GM_EARTH)

(Default: SatelliteDynamics.GM_EARTH

Return:

  * `a::AbstractArray{<:Real, 1}`: Acceleration in X, Y, and Z inertial directions [m/s^2]
