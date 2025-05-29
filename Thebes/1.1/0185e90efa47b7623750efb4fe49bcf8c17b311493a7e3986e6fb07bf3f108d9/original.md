```
rotateby(pt::Point3D, angleX, angleY, angleZ)
rotateby(ptlist::Array{Point3D, 1}, angleX, angleY, angleZ)
rotateby(point::Point3D, r::Rotation)
rotateby(ptlist::Array{Point3D, 1}, r::Rotation)
```

Return a new point/list of points resulting from rotating around the x, y, and z axes by angleX, angleY, angleZ.

The Z rotation is first, then the Y, then the X.

A 3×3 rotation matrix parameterized by the "Tait-Bryant" XYZ Euler angle convention, consisting of first a rotation about the Z axis by theta3, followed by a rotation about the Y axis by theta2, and finally a rotation about the X axis by theta1.
