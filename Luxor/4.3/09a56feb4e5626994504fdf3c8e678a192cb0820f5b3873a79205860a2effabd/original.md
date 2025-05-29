```
juliacircles(radius=100;
    outercircleratio=0.75,
    innercircleratio=0.65,
    action=:fill)
```

Draw the three Julia circles ("dots") in color centered at the origin.

The distance of the centers of each circle from the origin is `radius`.

The optional keyword argument `outercircleratio` (default 0.75) determines the radius of each circle relative to the main radius. So the default is to draw circles of radius 75 points around a larger circle of radius 100.

Return the three centerpoints.

The `innercircleratio` (default 0.65) no longer does anything useful (it used to draw the smaller circles) and will be deprecated.
