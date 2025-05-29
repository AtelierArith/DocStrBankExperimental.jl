```
dlength(body::Body/BodyList[;axes=:inertial]) -> Vector{Float64}
```

Compute the lengths of the faces on the perimeter of body `body`, whose ends are at the current `xend` and `yend` coordinates (in inertial space) of the body. Face 1 corresponds to the face between endpoints 1 and 2, for example. If `axes=:body`, uses the reference coordinates in body-fixed space.
