```
SteadyRotYTransformation(t0, ω, θ)
```

Construct a transformation of a reference frame rotating about the y axis at a constant rate `ω`.

The rotation angle as a function of time will be `angle = ω*(t - t0) + θ`.

# Arguments

  * `t0`: Time at which the angle between the target and source coordinate systems' x and z axes is θ.
  * `ω`: Rotation rate of the target coordinate system, in units of `rad/<time>`.
  * `θ`: Angle between the target and source coordinate systems' x and z axes at time `t0`.
