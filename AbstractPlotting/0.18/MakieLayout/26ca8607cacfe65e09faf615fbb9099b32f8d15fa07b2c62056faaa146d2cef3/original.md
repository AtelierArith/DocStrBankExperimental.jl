```
hlines!(ax::Axis, ys; xmin = 0.0, xmax = 1.0, attrs...)
```

Create horizontal lines across `ax` at `ys` in data coordinates and `xmin` to `xmax` in axis coordinates (0 to 1). All three of these can have single or multiple values because they are broadcast to calculate the final line segments.
