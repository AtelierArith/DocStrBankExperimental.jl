```
rigid_transform!(at::AtomTable{T}, transform::RigidTransform{T})
rigid_transform!(ac::AbstractAtomContainer, transform::RigidTransform)
```

指定されたコンテナのすべての原子に対して、`transform`（この順序で表される回転と平行移動）を適用します。
