```
curvature(body::Body/BodyList[;axes=:inertial]) -> Vector{Float64}
```

Compute the current curvature of the faces on the perimeter of body `body`. Face 1 corresponds to the face between points 1 and 2, for example. For an `OpenBody`, this provides a vector that is one element shorter than the number of points.
