```
struct RotationVec{T} <: Rotation{3,T}
RotationVec(sx, sy, sz)
```

Rodrigues vector parameterization of a 3×3 rotation matrix. The direction of the vector [sx, sy, sz] defines the axis of rotation, and the rotation angle is given by its norm.
