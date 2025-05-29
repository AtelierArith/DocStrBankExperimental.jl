```
arc2sagitta(p1::Point, p2::Point, s;
    action=:none)
```

Make a clockwise arc starting at `p1` and ending at `p2` that reaches a height of `s`, the sagitta, at the middle, and add it to the current path.

Return tuple of the center point and the radius of the arc.
