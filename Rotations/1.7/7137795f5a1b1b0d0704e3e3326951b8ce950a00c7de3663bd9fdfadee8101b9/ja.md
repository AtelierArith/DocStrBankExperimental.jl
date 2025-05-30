```
struct RotYX{T} <: Rotation{3,T}
RotYX(theta_y, theta_x)
```

X軸周りの`theta_x`の回転の後にY軸周りの`theta_y`の回転を表す3×3回転行列。
