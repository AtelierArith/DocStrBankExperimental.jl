```
ellipse(focus1::Point, focus2::Point, pt::Point;
    action=:none,
    stepvalue=pi/100,
    vertices=false,
    reversepath=false)
```

Build a polygon approximation to an ellipse, given two points and a point somewhere on the ellipse.
