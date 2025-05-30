```
struct RotXYZ{T} <: Rotation{3,T}
RotXYZ(theta1, theta2, theta3)
RotXYZ(roll=r, pitch=p, yaw=y)
```

「Tait-Bryant」XYZオイラー角の規約によってパラメータ化された3×3回転行列で、最初にZ軸周りに`theta3`だけ回転し、次にY軸周りに`theta2`だけ回転し、最後にX軸周りに`theta1`だけ回転します。

キーワード引数形式は、X、Y、Z軸にそれぞれロール、ピッチ、ヨーをXYZ順に適用します。（右手系座標系であるため、正のピッチは負のZ軸に向かうことに注意してください）。
