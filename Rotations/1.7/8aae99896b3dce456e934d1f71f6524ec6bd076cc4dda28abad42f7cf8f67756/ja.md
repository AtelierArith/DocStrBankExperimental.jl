```
struct RotYXZ{T} <: Rotation{3,T}
RotYXZ(theta1, theta2, theta3)
RotYXZ(roll=r, pitch=p, yaw=y)
```

"テイト・ブライアント" YXZオイラー角の規約によってパラメータ化された3×3回転行列で、最初にZ軸周りに`theta3`だけ回転し、次にX軸周りに`theta2`だけ回転し、最後にY軸周りに`theta1`だけ回転します。

キーワード引数形式は、YXZ順にそれぞれX、Y、Z軸にロール、ピッチ、ヨーを適用します。（右手座標系であるため、正のピッチは負のZ軸の方向を向いていることに注意してください）。
