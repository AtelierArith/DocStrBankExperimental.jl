```
isrot(m, ntol, dtol)
```

Indicate whether a 3×3 matrix is a rotation matrix.

### Arguments

  * `m`: A matrix to be tested
  * `ntol`: Tolerance for the norms of the columns of `m`
  * `dtol`: Tolerance for the determinant of a matrix whose columns are the unitized columns of `m`

### Output

Returns `true` if `m` is a rotation matrix.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/isrot_c.html)
