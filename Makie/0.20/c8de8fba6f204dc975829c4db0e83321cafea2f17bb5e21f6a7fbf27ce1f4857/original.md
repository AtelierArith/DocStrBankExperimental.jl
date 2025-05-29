```
vspan(xs_low, xs_high; ymin = 0.0, ymax = 1.0, attrs...)
```

Create vertical bands spanning across a `Scene` with 2D projection. The bands will be placed from `xs_low` to `xs_high` in data coordinates and `ymin` to `ymax` in scene coordinates (0 to 1). All four of these can have single or multiple values because they are broadcast to calculate the final spans.

All style attributes are the same as for `Poly`.
