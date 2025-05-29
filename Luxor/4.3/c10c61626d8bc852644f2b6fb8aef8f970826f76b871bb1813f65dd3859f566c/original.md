```
makebezierpath(pgon::Vector{Point};
    smoothing=1.0)
```

Return a Bézier path (a BezierPath) that represents a polygon (an array of points). The Bézier path is an array of segments (tuples of 4 points); each segment contains the four points that make up a section of the entire Bézier path.

`smoothing` determines how closely the curve follows the polygon. A value of 0 returns a straight-sided path; as values move above 1 the paths deviate further from the original polygon's edges.
