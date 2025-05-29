```
rebase_from_inertial_to_reference(Xi_to_A::MotionTransform,x::AbstractVector,m::RigidBodyMotion,reference_body::Int)
```

If `Xi_to_A` represents a motion transform from the inertial coordinates to some other coordinates A, such as that of a body, then this function returns a motion transform from the reference body coordinates to coordinates A. It uses the current joint state vector `x` to construct the transform list of the system `m`.
