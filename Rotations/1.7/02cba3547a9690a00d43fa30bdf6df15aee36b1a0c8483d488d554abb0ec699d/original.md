```
struct RotXZ{T} <: Rotation{3,T}
RotXZ(theta_x, theta_z)
```

A 3×3 rotation matrix which represents a rotation by `theta_z` about the Z axis, followed by a rotation by `theta_x` about the X axis.
