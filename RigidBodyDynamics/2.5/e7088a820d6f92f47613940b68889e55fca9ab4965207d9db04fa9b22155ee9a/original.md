```julia
attach!(
    mechanism,
    predecessor,
    successor,
    joint;
    joint_pose,
    successor_pose
)

```

Attach `successor` to `predecessor` using `joint`.

See [`Joint`](@ref) for definitions of the terms successor and predecessor.

The `Transform3D`s `joint_pose` and `successor_pose` define where `joint` is attached to each body. `joint_pose` should define `frame_before(joint)` with respect to any frame fixed to `predecessor`, and likewise `successor_pose` should define any frame fixed to `successor` with respect to `frame_after(joint)`.

`predecessor` is required to already be among the bodies of the `Mechanism`.

If `successor` is not yet a part of the `Mechanism`, it will be added to the `Mechanism`. Otherwise, the `joint` will be treated as a non-tree edge in the `Mechanism`, effectively creating a loop constraint that will be enforced using Lagrange multipliers (as opposed to using recursive algorithms).
