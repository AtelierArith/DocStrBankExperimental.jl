```
struct RotZYX{T} <: Rotation{3,T}
RotZYX(theta1, theta2, theta3)
RotZYX(roll=r, pitch=p, yaw=y)
```

A 3×3 rotation matrix parameterized by the "Tait-Bryant" ZYX Euler angle convention, consisting of first a rotation about the X axis by `theta3`, followed by a rotation about the Y axis by `theta2`, and finally a rotation about the Z axis by `theta1`.

The keyword argument form applies roll, pitch and yaw to the X, Y and Z axes respectively, in ZYX order. (Because it is a right-handed coordinate system, note that positive pitch is heading in the negative Z axis).
