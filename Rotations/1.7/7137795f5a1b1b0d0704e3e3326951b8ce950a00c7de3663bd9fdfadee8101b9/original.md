```
struct RotYX{T} <: Rotation{3,T}
RotYX(theta_y, theta_x)
```

A 3×3 rotation matrix which represents a rotation by `theta_x` about the X axis, followed by a rotation by `theta_y` about the Y axis.
