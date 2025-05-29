```
rotationmatrix_normalized(q::Quaternion)
```

Return a 3×3 matrix representing the rotation encoded by quaternion `q`. The function assumes that the quaternion is normalized. This is the case if `q` is a composition of rotations built using the functions `qrotation_x`, `qrotation_y`, and `qrotation_z`.
