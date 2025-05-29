```
arccoord(body::Body/BodyList[;axes=:inertial]) -> Vector{Float64}
```

Returns a vector containing the arclength coordinate along the surface of `body`, evaluated at the second endpoint of each face. So, e.g., the first coordinate would be the length of face 1, the second the length of face 2, and the last would be total length of all of the faces. Use inertial components (if `axes=:inertial`) or body-fixed components (if `axes=:body`). If this is a body list, restart the origin of the coordinates on each body in the list.
