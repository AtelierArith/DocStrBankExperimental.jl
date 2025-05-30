```
struct RotZXY{T} <: Rotation{3,T}
RotZXY(theta1, theta2, theta3)
RotZXY(roll=r, pitch=p, yaw=y)
```

"テイト・ブライアント" ZXY オイラー角の規約によってパラメータ化された 3×3 回転行列で、最初に Y 軸まわりに `theta3` の回転を行い、次に X 軸まわりに `theta2` の回転を行い、最後に Z 軸まわりに `theta1` の回転を行います。

キーワード引数形式は、ZXY 順序でそれぞれ X、Y、Z 軸にロール、ピッチ、ヨーを適用します。（右手系座標系であるため、正のピッチは負の Z 軸に向かうことに注意してください）。
