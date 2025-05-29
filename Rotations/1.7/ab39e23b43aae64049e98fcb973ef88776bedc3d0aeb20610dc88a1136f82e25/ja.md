```
struct RotYZ{T} <: Rotation{3,T}
RotYZ(theta_y, theta_z)
```

Z軸周りの`theta_z`の回転の後、Y軸周りの`theta_y`の回転を表す3×3回転行列。
