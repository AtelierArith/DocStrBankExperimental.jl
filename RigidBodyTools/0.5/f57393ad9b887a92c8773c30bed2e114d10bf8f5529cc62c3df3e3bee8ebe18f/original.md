```
arccoordmid(body::Body/BodyList[;axes=:inertial]) -> Vector{Float64}
```

Returns a vector containing the arclength coordinate along the surface of `body`, evaluated at the midpoints between the ends of faces. So, e.g., the first coordinate would be half of the length of face 1, the second would be half of face 2 plus all of face 1, etc. Use inertial components (if `axes=:inertial`) or body-   fixed components (if `axes=:body`). If this is a body list, restart   the origin of the coordinates on each body in the list.
