Perform spherical linear interpolation (SLERP) on two quaternions. Interpolatles  from quaternion, `q1`, to quaternion, `q2`, at normalized interpolation time, `t`.

Interpolation time must be in the range `[0, 1]` a value of `0` will return `q1`, while a value of `1` will return `q2`.

Arguments:

  * `q1::Quaternion`: Starting Quaternion
  * `q2::Quaternion`: Ending Quaternion
  * `t::Real`: Normalized interpolation time. [0, 1]

Returns:

  * `q:Quaternion`: Quaternion attitude interpolation from q1 toward q2 at time t.
