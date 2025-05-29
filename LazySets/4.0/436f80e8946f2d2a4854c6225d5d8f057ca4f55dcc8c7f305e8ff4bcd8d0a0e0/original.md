```
normalize(P::AbstractHPolygon{N}, p::Real=N(2)) where {N}
```

Normalize a polygon in constraint representation.

### Input

  * `P` – polygon in constraint representation
  * `p` – (optional, default: `2`) norm

### Output

A new polygon in constraint representation whose normal directions $a_i$ are normalized, i.e., such that $‖a_i‖_p = 1$ holds.
