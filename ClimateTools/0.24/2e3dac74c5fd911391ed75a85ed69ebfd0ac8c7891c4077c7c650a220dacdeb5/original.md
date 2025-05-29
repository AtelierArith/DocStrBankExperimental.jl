```
inpoly(p, poly::Matrix)
```

Determines if a point is inside a polygon.

  * p – point (x,y) or [x,y]
  * poly – polygon vertices [x1 x2 ... xn x1                           y1 y2 ... yn y1]

Returns true if point has an odd winding number.  This should label points as exterior which are inside outcrops.  See test for a test.

Author: Github "Mauro3" / "Mauro"
