```
setbezierhandles(bps::BezierPathSegment;
        angles  = [0.05, -0.1],
        handles = [0.3, 0.3])
```

Return a new BezierPathSegment with new locations for the Bezier control points in the BezierPathSegment `bps`.

`angles` are the two angles that the "handles" make with the line direciton.

`handles` are the lengths of the "handles". 0.3 is a typical value.
