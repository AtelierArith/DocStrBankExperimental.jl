```
rotateby!(ptlist::Array{Point3D, 1}, existingpt::Point3D, angleX, angleY, angleZ)
rotateby!(ptlist::Array{Point3D, 1}, existingpt::Point3D, r::Rotation)
rotateby!(ptlist::Array{Point3D, 1}, r::Rotation=RotXYZ{Float64})
```

Rotate each point in the list by rotation (or angleX, angleY, angleZ) around another point (or origin).
