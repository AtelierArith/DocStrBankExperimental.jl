```
eul2xf(eulang, axisa, axisb, axisc)
```

Compute a state transformation from an Euler angle factorization of a rotation and the derivatives of those Euler angles.

### Arguments

  * `eulang`: An array of Euler angles and their derivatives
  * `axisa`: Axis A of the Euler angle factorization
  * `axisb`: Axis B of the Euler angle factorization
  * `axisc`: Axis C of the Euler angle factorization

### Output

Returns a state transformation matrix.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/eul2xf_c.html)
