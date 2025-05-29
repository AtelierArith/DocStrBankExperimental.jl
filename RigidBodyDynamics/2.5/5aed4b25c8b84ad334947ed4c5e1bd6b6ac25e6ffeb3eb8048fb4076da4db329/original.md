```julia
bias_acceleration(state, joint)
bias_acceleration(state, joint, safe)

```

Return the bias acceleration across the given joint, i.e. the spatial acceleration of `frame_after(joint)` with respect to `frame_before(joint)`, expressed in the root frame of the mechanism when all joint accelerations are zero.
