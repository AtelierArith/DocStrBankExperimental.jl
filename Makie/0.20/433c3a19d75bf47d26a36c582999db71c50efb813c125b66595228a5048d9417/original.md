```
vlines(xs; ymin = 0.0, ymax = 1.0, attrs...)
```

Create vertical lines across a `Scene` with 2D projection. The lines will be placed at `xs` in data coordinates and `ymin` to `ymax` in scene coordinates (0 to 1). All three of these can have single or multiple values because they are broadcast to calculate the final line segments.

All style attributes are the same as for `LineSegments`.
