```
rotation_about_z(θ::Real) -> SMatrix{3,3}
```

Constructs the rotation matrix corresponding to rotation about the z axis by angle θ.  The matrix transforms the coordinates of a vector in system A to coordinates in system B, where Θ is the angle of A with respect to B. (Flip the sign of the input Θ if you want it to correspond to B's angle relative to A.)
