```
overapproximate(X::LazySet{N}, dirs::AbstractDirections;
                [prune]::Bool=true) where {N}
```

Overapproximate a (possibly unbounded) set with template directions.

### Input

  * `X`     – set
  * `dirs`  – directions
  * `prune` – (optional, default: `true`) flag for removing redundant constraints

### Output

A polyhedron overapproximating the set `X` with the directions from `dirs`. The overapproximation is computed using the support function. The result is an `HPolytope` if it is bounded and otherwise an `HPolyhedron`.
