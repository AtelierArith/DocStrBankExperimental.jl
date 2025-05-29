```
body_transforms(x::AbstractVector,ls::RigidBodyMotion) -> MotionTransformList
```

Parse the overall state vector `x` into the individual joints and construct the inertial system-to-body transforms for every body. Return these transforms in a `MotionTransformList`.
