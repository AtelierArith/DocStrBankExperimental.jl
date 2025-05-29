```
struct RotZY{T} <: Rotation{3,T}
RotZY(theta_z, theta_y)
```

A 3×3 rotation matrix which represents a rotation by `theta_y` about the Y axis, followed by a rotation by `theta_z` about the Z axis.
