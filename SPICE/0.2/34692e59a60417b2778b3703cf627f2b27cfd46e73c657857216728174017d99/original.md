```
rotvec(v1, angle, iaxis)
```

Transform a vector to a new coordinate system rotated by `angle` radians about axis `iaxis`. This transformation rotates `v1` by `-angle` radians about the specified axis.

### Arguments

  * `v1`: Vector whose coordinate system is to be rotated
  * `angle`: Angle of rotation in radians
  * `iaxis`: Axis of rotation (X=1, Y=2, Z=3)

### Output

Returns the resulting vector expressed in the new coordinate system.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/rotvec_c.html)
