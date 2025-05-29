```
arclength(bl::BodyList[;axes=:inertial]) -> Vector{Float64}
```

Compute the total arclength of each body in `bl` and assemble the results into a vector. If `axes=:body`, use the body-fixed coordinates.
