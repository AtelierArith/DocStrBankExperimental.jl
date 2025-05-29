```julia
bias_acceleration(state, body)
bias_acceleration(state, body, safe)

```

Return the bias acceleration of the given body with respect to the world, i.e. the spatial acceleration of `default_frame(body)` with respect to the root frame of the mechanism, expressed in the root frame, when all joint accelerations are zero.
