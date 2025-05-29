```julia
joint_transform(state, joint)
joint_transform(state, joint, safe)

```

Return the joint transform for the given joint, i.e. the transform from `frame_after(joint)` to `frame_before(joint)`.
