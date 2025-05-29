```
RodObstacle(p1, p2, radius; inverted = false) <: AbstractObstacle
```

Construct a spherocylindrical rod between points `p1` and `p2` with thickness `2*radius`. With `inverted = true`, the obstacle is the entire space *except* the spherocylinder.
