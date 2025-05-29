```
xf2eul(xform, axisa, axisb, axisc)
```

Convert a state transformation matrix to Euler angles and their derivatives with respect to a specified set of axes.

### Arguments

  * `xform`: A state transformation matrix
  * `axisa`: Axis A of the Euler angle factorization
  * `axisb`: Axis B of the Euler angle factorization
  * `axisc`: Axis C of the Euler angle factorization

### Output

Returns a tuple of an array of Euler angles and their derivatives and a boolean that indicates whether these are a unique representation.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/xf2eul_c.html)
