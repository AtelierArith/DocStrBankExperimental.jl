```
rigid_transform!(at::AtomTable{T}, transform::RigidTransform{T})
rigid_transform!(ac::AbstractAtomContainer, transform::RigidTransform)
```

Applies the rotation and the translation represented by `transform` (in this order) to all atoms of the given container.
