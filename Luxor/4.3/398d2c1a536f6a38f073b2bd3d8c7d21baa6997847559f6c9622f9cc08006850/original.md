```
drawpath(path::Path, k::Real;
    steps=10, # used when approximating Bezier curve segments
    action=:none,
    startnewpath=true,
    pathlength = 0.0)
```

Draw the path in `path` starting at the beginning and stopping at `k` between 0 and 1. So if `k` is 0.5, half the path is drawn.

Returns the last point processed.

The function calculates the length of the entire path before drawing it. If you want to draw a large path more than once, it might be more efficient to calculate the length of the path first, and provide it to the `pathlength` keyword.

The `steps` parameter is used when approximating the length of any curve (Bezier) sections. Higher values will be more accurate.
