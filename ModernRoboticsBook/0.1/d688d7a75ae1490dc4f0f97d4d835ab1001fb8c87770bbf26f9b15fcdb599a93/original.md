```
EulerStep(thetalist, dthetalist, ddthetalist, dt)
```

Compute the joint angles and velocities at the next timestep using first order Euler integration.

# Arguments

  * `thetalist`: the $n$-vector of joint variables.
  * `dthetalist`: the $n$-vector of joint rates.
  * `ddthetalist`: the $n$-vector of joint accelerations.
  * `dt`: the timestep delta t.

# Return

  * `thetalistNext`: the vector of joint variables after `dt` from first order Euler integration.
  * `dthetalistNext`: the vector of joint rates after `dt` from first order Euler integration.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> EulerStep([0.1, 0.1, 0.1], [0.1, 0.2, 0.3], [2, 1.5, 1], 0.1)
([0.11000000000000001, 0.12000000000000001, 0.13], [0.30000000000000004, 0.35000000000000003, 0.4])
```
