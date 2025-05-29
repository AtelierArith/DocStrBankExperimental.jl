```
vlines!(ax::Axis, xs; ymin = 0.0, ymax = 1.0, attrs...)
```

Create vertical lines across `ax` at `xs` in data coordinates and `ymin` to `ymax` in axis coordinates (0 to 1). All three of these can have single or multiple values because they are broadcast to calculate the final line segments.
