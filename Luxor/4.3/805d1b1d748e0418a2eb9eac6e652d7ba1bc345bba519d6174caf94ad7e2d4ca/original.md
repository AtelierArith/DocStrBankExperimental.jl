```
bezierstroke(point1, point2, width=0.0)
```

Return a BezierPath, a stroked version of a straight line between two points.

It wil have 2 or 6 Bezier path segments that define a brush or pen shape. If width is 0, the brush shape starts and ends at a point. Otherwise the brush shape starts and ends with the thick end.

To draw it, use eg `drawbezierpath(..., :fill)`.
