```
arc2r(c1::Point, p2::Point, p3::Point; action=:none)
arc2r(c1::Point, p2::Point, p3::Point, action)
```

Add a circular arc centered at `c1` that starts at `p2` and ends at `p3`, going clockwise, to the current path.

`c1`-`p2` really determines the radius. If `p3` doesn't lie on the circular path, it will be used only as an indication of the arc's length, rather than its position.
