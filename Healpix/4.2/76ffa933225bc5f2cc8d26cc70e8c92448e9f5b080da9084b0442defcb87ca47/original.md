```
equiprojinv(x, y)
```

Inverse equirectangular projection. Given a point (x, y) on the plane [-1, 1] × [-1, 1], return a tuple (Bool, Number, Number) where the first Boolean is a flag telling if the point falls within the projection (true) or not (false), and the two numbers are the latitude and longitude in radians.
