```
setbezierhandles(bezpath::BezierPath;
    angles=[0 .05, -0.1],
    handles=[0.3, 0.3])
```

Return a new BezierPath with new locations for the Bézier control points in every Bézier path segment of the BezierPath in `bezpath`.

`angles` are the two angles that the "handles" make with the line direciton.

`handles` are the lengths of the "handles". 0.3 is a typical value.
