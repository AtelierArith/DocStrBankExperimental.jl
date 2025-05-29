```
bezierfrompoints(startpoint::Point,
    pointonline1::Point,
    pointonline2::Point,
    endpoint::Point)
```

Given four points, return the Bézier curve that passes through all four points, starting at `startpoint` and ending at `endpoint`. The two middle points of the returned BezierPathSegment are the two control points that make the curve pass through the two middle points supplied.
