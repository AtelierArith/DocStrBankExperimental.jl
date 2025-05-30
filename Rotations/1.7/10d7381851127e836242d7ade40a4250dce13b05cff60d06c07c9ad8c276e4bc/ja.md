```
struct RotZY{T} <: Rotation{3,T}
RotZY(theta_z, theta_y)
```

Y軸周りに`theta_y`だけ回転し、その後Z軸周りに`theta_z`だけ回転する3×3回転行列です。
