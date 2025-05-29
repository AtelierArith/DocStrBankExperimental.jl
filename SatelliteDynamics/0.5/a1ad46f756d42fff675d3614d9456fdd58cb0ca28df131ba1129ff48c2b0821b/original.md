Computes the perturbing, non-conservative acceleration caused by atmospheric drag assuming that the ballistic properties of the spacecraft are captured by the coefficient of drag.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: Satellite Cartesean state in the inertial reference frame [m; m/s]
  * `rho::Real`: atmospheric density [kg/m^3]
  * `mass::Real`: Spacecraft mass [kg]
  * `area::Real`: Wind-facing cross-sectional area [m^2]
  * `Cd::Real`: coefficient of drag [dimensionless]
  * `T::AbstractArray{<:Real, 2}`: Rotation matrix from the inertial to the true-of-date frame

Return:

  * `a::AbstractArray{<:Real, 1}`: Acceleration due to drag in the X, Y, and Z inertial directions. [m/s^2]

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.83-86.
