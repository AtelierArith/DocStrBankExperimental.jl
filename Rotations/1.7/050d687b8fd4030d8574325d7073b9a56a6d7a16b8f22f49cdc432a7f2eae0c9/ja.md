```
struct RotZXY{T} <: Rotation{3,T}
RotZXY(theta1, theta2, theta3)
RotZXY(roll=r, pitch=p, yaw=y)
```

"テイト・ブライアント" ZXY オイラー角の規約によってパラメータ化された 3×3 回転行列で、最初に `theta3` による Y 軸周りの回転、次に `theta2` による X 軸周りの回転、最後に `theta1` による Z 軸周りの回転が行われます。

キーワード引数形式は、ZXY 順序でそれぞれ X、Y、Z 軸にロール、ピッチ、ヨーを適用します。（右手系座標系であるため、正のピッチは負の Z 軸に向かうことに注意してください）。
