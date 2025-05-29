```
struct RotZX{T} <: Rotation{3,T}
RotZX(theta_z, theta_x)
```

X軸周りに`theta_x`だけ回転し、その後Z軸周りに`theta_z`だけ回転する3×3回転行列。
