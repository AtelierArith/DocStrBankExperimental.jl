Computes the accleration caused by Earth gravity as modeled by a spherical  harmonic gravity field.

Arguments:

  * `r_sat::AbstractArray{<:Real, 1}`: Satellite position in the inertial frame [m]
  * `R_eci_ecef::AbstractArray{<:Real, 2}`: Rotation matrix transforming a vector from the inertial to body-fixed reference frames.
  * `n_max::Integer`: Maximum degree coefficient to use in expansion
  * `m_max::Integer`: Maximum order coefficient to use in the expansion. Must be less than the degree.

Return:

  * `a::AbstractArray{<:Real, 1}`: Gravitational acceleration in X, Y, and Z inertial directions [m/s^2]

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.56-68.
