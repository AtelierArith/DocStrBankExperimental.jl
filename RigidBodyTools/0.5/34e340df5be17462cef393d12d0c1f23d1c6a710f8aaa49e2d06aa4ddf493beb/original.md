```
tangent(body::Body/BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

Compute the current tangent in inertial components (if `axes=:inertial`) or body-   fixed components (if `axes=:body`) of the faces on the perimeter of body `body`, whose ends are at the current `xend` and `yend` coordinates (in inertial space) of the body. Face 1 corresponds to the face between points 1 and 2, for example. For an `OpenBody`, this provides a vector that is one element shorter than the number of points.
