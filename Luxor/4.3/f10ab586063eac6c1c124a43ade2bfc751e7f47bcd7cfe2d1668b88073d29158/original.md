```
hypotrochoid(R, r, d;
    action=:none,
    stepby=0.01,
    period=0.0,
    vertices=false)
hypotrochoid(R, r, d, action;
    stepby=0.01,
    period=0.0,
    vertices=false)
```

Make a hypotrochoid with short line segments, and add it to the current path. (Like a Spirograph.) The curve is traced by a point attached to a circle of radius `r` rolling around the inside  of a fixed circle of radius `R`, where the point is a distance `d` from  the center of the interior circle. Things get interesting if you supply non-integral values.

Special cases include the hypocycloid, if `d` = `r`, and an ellipse, if `R` = `2r`.

`stepby`, the angular step value, controls the amount of detail, ie the smoothness of the polygon,

If `period` is not supplied, or 0, the lowest period is calculated for you.

The function can return a polygon (a list of points), or draw the points directly using the supplied `action`. If the points are drawn, the function returns a tuple showing how many points were drawn and what the period was (as a multiple of `pi`).
