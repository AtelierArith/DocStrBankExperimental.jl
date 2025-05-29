```
struct RotZXZ{T} <: Rotation{3,T}
RotZXZ(theta1, theta2, theta3)
```

「適切な」ZXZオイラー角の規約によってパラメータ化された3×3回転行列であり、最初にZ軸周りに`theta3`だけ回転し、次にX軸周りに`theta2`だけ回転し、最後にZ軸周りに`theta1`だけ回転します。
