```
spline(x, y, m, method)
```

Generate a cubic spline-fit, starting from the first data point and ending at the last data point.

**Parameters:**

`x` :     A list containing the X coordinates `y` :     A list containing the Y coordinates `m` :     The number of points in the polygon to be drawn (`m` > len(`x`)) `method` :     The smoothing method

The values for `x` and `y` are in world coordinates. The attributes that control the appearance of a spline-fit are linetype, linewidth and color index.

If `method` is > 0, then a generalized cross-validated smoothing spline is calculated. If `method` is 0, then an interpolating natural cubic spline is calculated. If `method` is < -1, then a cubic B-spline is calculated.
