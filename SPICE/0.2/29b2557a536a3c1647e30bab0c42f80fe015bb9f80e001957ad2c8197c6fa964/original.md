```
rotmat(m1, angle, iaxis)
```

Applies a rotation of `angle` radians about axis `iaxis` to a matrix `m1`. This rotation is thought of as rotating the coordinate system.

### Arguments

  * `m1`: Matrix to be rotated
  * `angle`: Angle of rotation (radians)
  * `iaxis`: Axis of rotation (X=1, Y=2, Z=3)

### Output

Returns the resulting rotated matrix.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/rotmat_c.html)
