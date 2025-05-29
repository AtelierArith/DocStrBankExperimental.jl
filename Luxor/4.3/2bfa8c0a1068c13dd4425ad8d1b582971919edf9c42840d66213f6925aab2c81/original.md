```
circlepath(center::Point, radius;
    action=:none,
    reversepath=false,
    kappa = 0.5522847498307936)
circlepath(center::Point, radius, action;
    reversepath=false,
    kappa = 0.5522847498307936)
```

Make a circle using Bézier curves, and add it to the current path.

One benefit of using this rather than `circle()` is that you can use the `reversepath` option to draw the circle clockwise rather than `circle`'s counterclockwise.

The magic value, `kappa`, is `4.0 * (sqrt(2.0) - 1.0) / 3.0`.

Return two points, the corners of a bounding box.
