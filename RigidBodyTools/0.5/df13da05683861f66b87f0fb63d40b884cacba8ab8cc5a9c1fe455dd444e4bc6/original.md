```
transform_body!(b::Body,T::MotionTransform)
```

Transforms a body's own coordinate system (in-place) using the given `MotionTransform`. This function differs from [`update_body!`](@ref) because it changes the coordinates of the body in its own coordinate system, whereas the latter function only changes the inertial coordinates of the body. `T` is interpreted as a transform from the new system to the old system.
