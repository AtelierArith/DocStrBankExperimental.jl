```
bezierpathtopoly(bezierpath::BezierPath;
    steps=10)
```

Convert a Bézier path (an array of BezierPathSegments, where each is a tuple of four points: anchor1, control1, control2, anchor2), to a polygon.

To make a Bézier path, use `makebezierpath()` on a polygon.

The `steps` optional keyword determines how many straight line sections are used for each path.
