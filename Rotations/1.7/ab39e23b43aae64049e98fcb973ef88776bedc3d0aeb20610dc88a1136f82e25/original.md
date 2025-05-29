```
struct RotYZ{T} <: Rotation{3,T}
RotYZ(theta_y, theta_z)
```

A 3×3 rotation matrix which represents a rotation by `theta_z` about the Z axis, followed by a rotation by `theta_y` about the Y axis.
