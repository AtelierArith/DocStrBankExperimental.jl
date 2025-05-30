```
struct RotXYX{T} <: Rotation{3,T}
RotXYX(theta1, theta2, theta3)
```

"適切な" XYX オイラー角の規約によってパラメータ化された 3×3 回転行列であり、最初に `theta3` による X 軸周りの回転、次に `theta2` による Y 軸周りの回転、最後に `theta1` による X 軸周りの回転が行われます。
