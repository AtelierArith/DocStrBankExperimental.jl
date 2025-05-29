```julia
transform(
    accel,
    old_to_new,
    twist_of_current_wrt_new,
    twist_of_body_wrt_base
)

```

Transform the `SpatialAcceleration` to a different frame.

The transformation rule is obtained by differentiating the transformation rule for twists.
