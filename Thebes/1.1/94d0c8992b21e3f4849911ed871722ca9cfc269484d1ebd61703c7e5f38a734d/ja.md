```
rotateby!(ptlist::Array{Point3D, 1}, existingpt::Point3D, angleX, angleY, angleZ)
rotateby!(ptlist::Array{Point3D, 1}, existingpt::Point3D, r::Rotation)
rotateby!(ptlist::Array{Point3D, 1}, r::Rotation=RotXYZ{Float64})
```

リスト内の各点を、別の点（または原点）を中心に回転（またはangleX、angleY、angleZ）します。
