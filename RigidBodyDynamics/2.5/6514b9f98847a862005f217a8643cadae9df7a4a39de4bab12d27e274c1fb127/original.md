```julia
body_fixed_frame_to_body(mechanism, frame)

```

Return the `RigidBody` to which `frame` is attached.

Note: this function is linear in the number of bodies and is not meant to be called in tight loops.
