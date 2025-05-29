```
twovec(axdef, indexa, plndef, indexp)
```

Find the transformation to the right-handed frame having a given vector as a specified axis and having a second given vector lying in a specified coordinate plane.

### Arguments

  * `axdef`: Vector defining a principal axis
  * `indexa`: Principal axis number of axdef (X=1, Y=2, Z=3)
  * `plndef`: Vector defining (with axdef) a principal plane
  * `indexp`: Second axis number (with indexa) of principal plane

### Output

Returns output rotation matrix.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/twovec_c.html)
