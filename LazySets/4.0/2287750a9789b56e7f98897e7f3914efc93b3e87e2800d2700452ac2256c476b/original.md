```
intersection(P1::Union{VPolygon, VPolytope}, P2::Union{VPolygon, VPolytope};
             [backend]=nothing, [prunefunc]=nothing)
```

Compute the intersection of two polytopes in vertex representation.

### Input

  * `P1`        – polytope in vertex representation
  * `P2`        – polytope in vertex representation
  * `backend`   – (optional, default: `nothing`) the backend for polyhedral                computations
  * `prunefunc` – (optional, default: `nothing`) function to prune the vertices                of the result

### Output

A `VPolytope`.

### Notes

If `prunefunc` is `nothing`, this implementation sets it to `(X -> removevredundancy!(X; tol=_ztol(eltype(P1))))`.
