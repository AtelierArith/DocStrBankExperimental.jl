```
hspan(ys_low, ys_high; xmin = 0.0, xmax = 1.0, attrs...)
```

Create horizontal bands spanning across a `Scene` with 2D projection. The bands will be placed from `ys_low` to `ys_high` in data coordinates and `xmin` to `xmax` in scene coordinates (0 to 1). All four of these can have single or multiple values because they are broadcast to calculate the final spans.

All style attributes are the same as for `Poly`.
