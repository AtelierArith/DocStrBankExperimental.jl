```
add_joint!(g::BVHGraph, v₋₁::Integer, name::AbstractString, off::Vector{Float64}, nb::Vector = outneighbors(g, v₋₁))
```

Add a vertex named `name` with offset `off` as an outneighbor to `v₋₁`.  The outneighbors of `v₋₁` that should be attached as outneighbors to the new vertex can be specified. 

"JOINT" is automatically added in front of `name`.  `v₋₁` can also be identified by its name.
