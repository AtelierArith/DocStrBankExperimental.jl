```
struct RotYXY{T} <: Rotation{3,T}
RotYXY(theta1, theta2, theta3)
```

"適切な" YXY オイラー角の規約によってパラメータ化された 3×3 回転行列であり、最初に Y 軸周りに `theta3` だけ回転し、次に X 軸周りに `theta2` だけ回転し、最後に Y 軸周りに `theta1` だけ回転します。
