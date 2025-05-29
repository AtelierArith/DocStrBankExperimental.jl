```
squircle(center::Point, hradius, vradius;
    action=:none,
    rt = 0.5, stepby = pi/40, vertices=false)
squircle(center::Point, hradius, vradius, action;
    rt = 0.5, stepby = pi/40, vertices=false)
```

Make a squircle or superellipse (basically a rectangle with rounded corners).  Specify the center position, horizontal radius (distance from center to a side), and vertical radius (distance from center to top or bottom):

The root (`rt`) option defaults to 0.5, and gives an intermediate shape. Values less than 0.5 make the shape more rectangular. Values above make the shape more round. The horizontal and vertical radii can be different.

This function generates a series of points and makes a polygon or returns an array of Points.

See also: `polysuper()` and `squirclepath()`.
