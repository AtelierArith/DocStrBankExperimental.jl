```
ConstantVelocityTransformation(t0, x0, v)
```

Construct a transformation of a reference frame moving with a constant velocity, i.e., `x_target = x_source + x0 .+ (t - t0)*v`.

# Arguments

  * `t0`: Time at which the position of the source coordinate system's origin in the target coordinate system is equal to `x0`.
  * `x0`: Position of the source coordinate system's origin in the target coordinate system's frame of reference at time `t0`.
  * `v`: (Constant) velocity of the source coordinate system relative to the target coordinate system.
