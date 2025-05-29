```
rotateby!(o::Object, pt::Point3D, angleX, angleY, angleZ)
rotateby!(o::Object, pt::Point3D, r::Rotation=RotXYZ(0, 0, 0))
```

Rotate an object around a point by rotation r, or angleX, angleY, angleZ.
