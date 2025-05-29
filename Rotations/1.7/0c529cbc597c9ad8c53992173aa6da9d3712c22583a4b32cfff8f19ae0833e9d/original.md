```
struct RotXY{T} <: Rotation{3,T}
RotXY(theta_x, theta_y)
```

A 3×3 rotation matrix which represents a rotation by `theta_y` about the Y axis, followed by a rotation by `theta_x` about the X axis.
