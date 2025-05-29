```
circletangent2circles(radius, circle1center::Point, circle1radius, circle2center::Point, circle2radius)
```

Find the centers of up to two circles of radius `radius` that are tangent to the two circles defined by `circle1...` and `circle2...`. These two circles can overlap, but one can't be inside the other.

  * (0, O, O)      - no such circles exist
  * (1, pt1, O)    - 1 circle exists, centered at pt1
  * (2, pt1, pt2)  - 2 circles exist, with centers at pt1 and pt2

(The O are just dummy points so that three values are always returned.)
