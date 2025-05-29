```
(T::MotionTransform)(b::Body) -> Body
```

Transforms a body `b` using the given `MotionTransform`, creating a copy of this body with the new configuration. In using this transform `T` (which defines a transform from system A to system B), A is interpreted as an inertial coordinate system and B as the body system. Thus, the position vector in `T` is interpreted as the relative position of the body in inertial coordinates and the inverse of the rotation operator is applied to transform body-fixed coordinates to the inertial frame.
