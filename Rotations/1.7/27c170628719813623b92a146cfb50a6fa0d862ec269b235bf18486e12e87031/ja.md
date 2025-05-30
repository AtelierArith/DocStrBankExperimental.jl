```
struct RotZYX{T} <: Rotation{3,T}
RotZYX(theta1, theta2, theta3)
RotZYX(roll=r, pitch=p, yaw=y)
```

"テイト・ブライアント" ZYX オイラー角の規約によってパラメータ化された 3×3 回転行列で、最初に `theta3` による X 軸周りの回転、次に `theta2` による Y 軸周りの回転、最後に `theta1` による Z 軸周りの回転が行われます。

キーワード引数形式は、ZYX 順に X、Y、Z 軸にそれぞれロール、ピッチ、ヨーを適用します。（右手座標系であるため、正のピッチは負の Z 軸に向かうことに注意してください）。
