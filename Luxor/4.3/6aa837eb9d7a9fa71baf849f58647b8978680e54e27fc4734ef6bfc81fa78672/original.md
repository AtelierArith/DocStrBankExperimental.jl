```
ellipse(focus1::Point, focus2::Point, k;
        action=:none,
        stepvalue=pi/100,
        vertices=false,
        reversepath=false)
```

Build a polygon approximation to an ellipse, given two points and a distance, `k`, which is the sum of the distances to the focii of any points on the ellipse (or the shortest length of string required to go from one focus to the perimeter and on to the other focus), and add it to the current path.
