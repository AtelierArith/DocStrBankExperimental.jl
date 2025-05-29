```
basis = basis_rotation(Ω, i, ω)
basis = basis_rotation(xvec, yvec)
basis_rotation() = one(RotMatrix{3, Float64})
```

From the RAAN `Ω`, inclination `i`, and argument of the periapsis `ω`, computes the rotation matrix that transforms  an orbit's perifocal plane to the inertial frame. For this matrix, the first column is a unit vector that points toward  the periapsis of the orbit, and the third column is a unit vector that points in the normal direction. 

If two vectors `xvec` and `yvec` are provided, a rotation matrix is constructed that describes the plane the two vectors define, where `normalize(xvec)` is the first basis vector.
