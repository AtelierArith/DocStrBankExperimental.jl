```
struct RotXYX{T} <: Rotation{3,T}
RotXYX(theta1, theta2, theta3)
```

A 3×3 rotation matrix parameterized by the "proper" XYX Euler angle convention, consisting of first a rotation about the X axis by `theta3`, followed by a rotation about the Y axis by `theta2`, and finally a rotation about the X axis by `theta1`.
