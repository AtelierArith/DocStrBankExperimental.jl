```
struct RotXY{T} <: Rotation{3,T}
RotXY(theta_x, theta_y)
```

Y軸周りの`theta_y`の回転の後、X軸周りの`theta_x`の回転を表す3×3の回転行列。
