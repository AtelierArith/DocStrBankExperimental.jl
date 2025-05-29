```
reflect_across_line(geom, dir; through_pt=nothing)
reflect_across_line(geom, p0, p1)
```

Return a copy of `geom` reflected across a line.

The line is specified through two points `p0` and `p1` that it passes through, or by a direction `dir` (vector or angle made with the x-axis) and a point `through_pt` that it passes through.
