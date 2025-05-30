```
struct RotXZY{T} <: Rotation{3,T}
RotXZY(theta1, theta2, theta3)
RotXZY(roll=r, pitch=p, yaw=y)
```

「テイト・ブライアント」XZYオイラー角の規約によってパラメータ化された3×3回転行列で、最初にY軸周りに`theta3`だけ回転し、次にZ軸周りに`theta2`だけ回転し、最後にX軸周りに`theta1`だけ回転します。

キーワード引数形式は、XZY順にX、Y、Z軸にそれぞれロール、ピッチ、ヨーを適用します。（右手系座標系であるため、正のピッチは負のZ軸に向かうことに注意してください）。
