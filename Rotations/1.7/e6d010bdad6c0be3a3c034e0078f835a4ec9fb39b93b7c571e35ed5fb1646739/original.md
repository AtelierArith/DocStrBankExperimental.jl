```
struct RotZX{T} <: Rotation{3,T}
RotZX(theta_z, theta_x)
```

A 3×3 rotation matrix which represents a rotation by `theta_x` about the X axis, followed by a rotation by `theta_z` about the Z axis.
