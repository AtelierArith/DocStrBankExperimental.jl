```
rotation_from_quaternion(q::SVector{4}) -> SMatrix{3,3}
```

Constructs a rotation matrix from a given quaternion `q` (a 4-dimensional vector). The matrix transforms the coordinates of a vector in system A to coordinates in system B, where A is rotated with respect to B by θ.
