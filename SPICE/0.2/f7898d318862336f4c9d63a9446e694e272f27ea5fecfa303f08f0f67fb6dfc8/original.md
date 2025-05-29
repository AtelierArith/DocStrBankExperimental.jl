```
inedpl(a, b, c, plane)
```

Find the intersection of a triaxial ellipsoid and a plane.

### Arguments

  * `a`: Length of ellipsoid semi-axis lying on the x-axis
  * `b`: Length of ellipsoid semi-axis lying on the y-axis
  * `c`: Length of ellipsoid semi-axis lying on the z-axis
  * `plane`: Plane that intersects ellipsoid

### Output

  * `ellipse`: Intersection ellipse

Returns `nothing` if no ellipse could be found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/inedpl_c.html)
