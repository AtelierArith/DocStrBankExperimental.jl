```
struct RotXZ{T} <: Rotation{3,T}
RotXZ(theta_x, theta_z)
```

Z軸周りの`theta_z`の回転の後、X軸周りの`theta_x`の回転を表す3×3回転行列。
