```
centraldiff(body::Body[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

Compute the circular central differences of coordinates on body `body` (or on each body in list `body`). If `axes=:body`, uses the reference coordinates in body-fixed space.
