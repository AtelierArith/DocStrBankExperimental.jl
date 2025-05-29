```
circlepointtangent(through::Point, radius, targetcenter::Point, targetradius)
```

Find the centers of up to two circles of radius `radius` that pass through point `through` and are tangential to a circle that has radius `targetradius` and center `targetcenter`.

This function returns a tuple:

  * (0, O, O)      - no circles exist
  * (1, pt1, O)    - 1 circle exists, centered at pt1
  * (2, pt1, pt2)  - 2 circles exist, with centers at pt1 and pt2

(The O are just dummy points so that three values are always returned.)
