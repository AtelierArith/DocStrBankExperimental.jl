```
vprjpi(vin, projpl, invpl)
```

Find the vector in a specified plane that maps to a specified vector in another plane under orthogonal projection.

### Arguments

  * `vin`: The projected vector
  * `projpl`: Plane containing `vin`
  * `invpl`: Plane containing inverse image of `vin`

### Output

Returns the inverse projection of `vin` or `nothing` if `vin` could not be calculated.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/vprjpi_c.html)
