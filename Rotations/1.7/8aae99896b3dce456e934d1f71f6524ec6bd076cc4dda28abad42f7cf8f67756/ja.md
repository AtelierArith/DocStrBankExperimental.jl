```
struct RotYXZ{T} <: Rotation{3,T}
RotYXZ(theta1, theta2, theta3)
RotYXZ(roll=r, pitch=p, yaw=y)
```

"テイト・ブライアント" YXZ オイラー角の規約によってパラメータ化された 3×3 回転行列で、最初に `theta3` による Z 軸周りの回転、次に `theta2` による X 軸周りの回転、最後に `theta1` による Y 軸周りの回転が行われます。

キーワード引数形式では、ロール、ピッチ、ヨーがそれぞれ X、Y、Z 軸に YXZ の順序で適用されます。（右手座標系であるため、正のピッチは負の Z 軸の方向を向いていることに注意してください）。
