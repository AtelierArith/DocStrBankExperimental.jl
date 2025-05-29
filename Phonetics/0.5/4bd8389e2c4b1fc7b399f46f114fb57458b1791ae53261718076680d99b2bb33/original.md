```
ellipsePts(f1, f2; percent=0.95, nPoints=500)
```

Calculates `nPoints` points of the perimeter of a data ellipse for `f1` and `f2` with approximately the percent of the data spcified by `percent` contained within the ellipse. Points are returned in counter-clockwise order as the polar angle of rotation moves from 0 to 2π.

See Friendly, Monette, and Fox (2013, Elliptical insights: Understanding statistical methods through elliptical geometry, Statistical science 28(1), 1-39) for more information on the calculation process.

# Args

  * `f1` The F1 values or otherwise x-axis values
  * `f2` The F2 values or otherwise y-axis values
  * `percent` (keyword) Percent of the data distribution the ellipse should approximately cover
  * `nPoints` (keyword) How many points to use when drawing the ellipse
