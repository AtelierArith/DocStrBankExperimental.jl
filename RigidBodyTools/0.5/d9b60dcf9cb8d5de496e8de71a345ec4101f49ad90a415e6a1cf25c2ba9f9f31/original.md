```
normalmid(body::Body/BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

Compute the current normals in inertial components (if `axes=:inertial`) or body-   fixed components (if `axes=:body`) of the faces formed between endpoints on the perimeter of body `body` (or each body in list `body`).
