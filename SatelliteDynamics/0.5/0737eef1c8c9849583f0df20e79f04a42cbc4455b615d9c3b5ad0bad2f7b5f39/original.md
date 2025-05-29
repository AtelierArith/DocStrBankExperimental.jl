Return Euler angles as a vector.

Equivalent to: `[e.phi, e.theta, e.psi]` for `EulerAngle` `e`

Arguments:

  * `e::EulerAngle` Euler Angle

Returns:

  * `evec::AbstractArray{Float64, 1}` Euler angles components in vector form.
