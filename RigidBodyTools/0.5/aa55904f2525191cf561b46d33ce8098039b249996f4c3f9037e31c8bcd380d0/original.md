```
midpoints(body::Body[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

Compute the x and y midpoints of the faces on the perimeter of body `body`, whose ends are at the current `x` and `y` coordinates (in inertial space) of the body (if `axes=:inertial`), or at the reference `x̃` and `ỹ` coordinates (body-fixed space) if `axes=:body`. Face 1 corresponds to the face between points 1 and 2, for example.

If `body` is a `BodyList`, then it computes the differences separately on each constituent body.
