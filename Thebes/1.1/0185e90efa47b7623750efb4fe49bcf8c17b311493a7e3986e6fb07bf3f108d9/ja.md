```
rotateby(pt::Point3D, angleX, angleY, angleZ)
rotateby(ptlist::Array{Point3D, 1}, angleX, angleY, angleZ)
rotateby(point::Point3D, r::Rotation)
rotateby(ptlist::Array{Point3D, 1}, r::Rotation)
```

新しい点/点のリストを返します。これは、angleX、angleY、angleZによってx、y、z軸の周りに回転した結果です。

Z回転が最初で、次にY、最後にXです。

「テイト・ブライアント」XYZオイラー角の規約によってパラメータ化された3×3回転行列で、最初にtheta3によるZ軸の回転、次にtheta2によるY軸の回転、最後にtheta1によるX軸の回転が含まれます。
