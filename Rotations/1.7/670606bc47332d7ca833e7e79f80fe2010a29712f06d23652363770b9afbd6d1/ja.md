```
struct RotXYX{T} <: Rotation{3,T}
RotXYX(theta1, theta2, theta3)
```

「適切な」XYXオイラー角の規約によってパラメータ化された3×3回転行列であり、最初に`theta3`によるX軸周りの回転、次に`theta2`によるY軸周りの回転、最後に`theta1`によるX軸周りの回転が行われます。
