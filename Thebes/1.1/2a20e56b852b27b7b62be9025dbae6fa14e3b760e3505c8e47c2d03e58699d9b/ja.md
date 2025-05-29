```
rotateby!(o::Object, pt::Point3D, angleX, angleY, angleZ)
rotateby!(o::Object, pt::Point3D, r::Rotation=RotXYZ(0, 0, 0))
```

オブジェクトを点を中心に回転r、またはangleX、angleY、angleZによって回転させます。
