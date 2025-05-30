```
struct RotXYZ{T} <: Rotation{3,T}
RotXYZ(theta1, theta2, theta3)
RotXYZ(roll=r, pitch=p, yaw=y)
```

「テイト・ブライアント」XYZオイラー角の規約によってパラメータ化された3×3回転行列で、最初に`theta3`によるZ軸周りの回転、次に`theta2`によるY軸周りの回転、最後に`theta1`によるX軸周りの回転が行われます。

キーワード引数形式は、XYZの順序でそれぞれX、Y、Z軸にロール、ピッチ、ヨーを適用します。（右手系座標系であるため、正のピッチは負のZ軸の方向を向いていることに注意してください）。
