```
add_joint!(g::BVHGraph, v₋₁::Integer, v₊₁::Integer, name::AbstractString; fraction::Float64 = 0.5)
```

Add a vertex on the straight line between `v₋₁` and `v₊₁` named `name`.  `fraction` refers to the fraction of the old offset that will be assigned to the new vertex.

"JOINT" is automatically added in front of `name`.  `v₋₁` and `v₊₁` can also be identified by their name.
