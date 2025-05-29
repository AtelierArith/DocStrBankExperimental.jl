```
equiproj(lat, lon)
```

Equirectangular projection. Given the latitude `lat` (in radians) and the longitude (in radians), return a tuple (Bool, Number, Number) where the first Boolean is a flag telling if the point falls within the projection (true) or not (false), and the two numbers are the x and y coordinates of the point on the projection plane (both are in the range [−1, 1]).
