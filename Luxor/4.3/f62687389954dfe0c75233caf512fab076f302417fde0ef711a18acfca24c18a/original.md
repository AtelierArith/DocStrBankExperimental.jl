```
circle(centerpoint::Point, r; action=:none)
circle(centerpoint::Point, r, action)
```

Make a circle of radius `r` centered at 'centerpoint', and add it to the current path.

`action` is one of the actions applied by `do_action()`, defaulting to `:none`.

Returns a tuple of two points, the corners of a bounding box that encloses the circle.

You can also use `ellipse()` to draw circles and place them by their centerpoint.

`circlepath()` builds a circle using Bézier curves, and add it to the current path.

`squircle()` builds a superellipse. `polysuper()` build a 'supershape', a generalization of the superellipse.

`juliacircles()` draws three circles in a familiar formation.

See also: `arc()`, `arc2r()`, `arc2sagitta()`, `carc()`, `carc2r()`, `carc2sagitta()`, `circlering()`, `crescent()`, `curve()`, `spiral()`, etc.
