```
struct RotYXY{T} <: Rotation{3,T}
RotYXY(theta1, theta2, theta3)
```

「適切な」YXYオイラー角の規約によってパラメータ化された3×3回転行列であり、最初にY軸周りに`theta3`だけ回転し、次にX軸周りに`theta2`だけ回転し、最後にY軸周りに`theta1`だけ回転します。
