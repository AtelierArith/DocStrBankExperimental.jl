```
is_isomorphic(D1::DeltaComplex, D2::DeltaComplex; kwargs..) :: Bool
```

Return `true` if `D1` is isomorph to `D2` up to a renaming of the vertices, edges and if `labeled_points=false` also points.

# Arguments

  * `labeled_points :: Bool = true` : If labeled_points is set to `false`, then the isomorphism also includes a renaming of the points.
