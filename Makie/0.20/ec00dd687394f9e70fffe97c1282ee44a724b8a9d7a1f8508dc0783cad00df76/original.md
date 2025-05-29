```
hlines(ys; xmin = 0.0, xmax = 1.0, attrs...)
```

Create horizontal lines across a `Scene` with 2D projection. The lines will be placed at `ys` in data coordinates and `xmin` to `xmax` in scene coordinates (0 to 1). All three of these can have single or multiple values because they are broadcast to calculate the final line segments.

All style attributes are the same as for `LineSegments`.
