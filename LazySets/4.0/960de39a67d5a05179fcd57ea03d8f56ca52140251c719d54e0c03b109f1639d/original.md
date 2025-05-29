```
translate(P::HPolygonOpt, v::AbstractVector; share::Bool=false)
```

Translate (i.e., shift) an optimized polygon in constraint representation by a given vector.

### Input

  * `P`     – optimized polygon in constraint representation
  * `v`     – translation vector
  * `share` – (optional, default: `false`) flag for sharing unmodified parts of            the original set representation

### Output

A translated optimized polygon in constraint representation.

### Notes

The normal vectors of the constraints (vector `a` in `a⋅x ≤ b`) are shared with the original constraints if `share == true`.

### Algorithm

We translate every constraint.
