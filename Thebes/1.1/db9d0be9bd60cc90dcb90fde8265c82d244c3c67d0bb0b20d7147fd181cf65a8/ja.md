```
rotateby(o::Object, pt::Point3D, angleX, angleY, angleZ)
rotateby(o::Object, pt::Point3D, r::Rotation=RotXYZ(0, 0, 0))
```

オブジェクトのコピーを点の周りに回転r、またはangleX、angleY、angleZによって回転させます。
