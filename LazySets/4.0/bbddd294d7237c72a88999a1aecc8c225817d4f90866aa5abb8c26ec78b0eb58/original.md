```
isbounded(P::AbstractHPolygon, [use_type_assumption]::Bool=true)
```

Determine whether a polygon in constraint representation is bounded.

### Input

  * `P`                   – polygon in constraint representation
  * `use_type_assumption` – (optional, default: `true`) flag for ignoring the                          type assumption that polygons are bounded

### Output

`true` if `use_type_assumption` is activated. Otherwise, `true` iff `P` is bounded.

### Algorithm

If `!use_type_assumption`, we use [`_isbounded_unit_dimensions`](@ref).
