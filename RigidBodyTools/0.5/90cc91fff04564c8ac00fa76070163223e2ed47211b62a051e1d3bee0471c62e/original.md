```
centraldiff(bl::BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

Compute the `centraldiff` on each constituent body in `bl`.  If `axes=:body`, uses the reference coordinates in body-fixed space.
