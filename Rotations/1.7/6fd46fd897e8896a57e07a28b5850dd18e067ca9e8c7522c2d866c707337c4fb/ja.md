```
struct RotXZX{T} <: Rotation{3,T}
RotXZX(theta1, theta2, theta3)
```

「適切な」XZXオイラー角の規約によってパラメータ化された3×3回転行列であり、最初にX軸周りに`theta3`だけ回転し、次にZ軸周りに`theta2`だけ回転し、最後にX軸周りに`theta1`だけ回転します。
