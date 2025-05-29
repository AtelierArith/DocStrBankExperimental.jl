```
struct RotZYZ{T} <: Rotation{3,T}
RotZYZ(theta1, theta2, theta3)
```

A 3×3 rotation matrix parameterized by the "proper" ZXZ Euler angle convention, consisting of first a rotation about the Z axis by `theta3`, followed by a rotation about the Y axis by `theta2`, and finally a rotation about the Z axis by `theta1`.
