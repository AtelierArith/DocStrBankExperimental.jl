```
overapproximate(X::LazySet{N}, dirs::Type{<:AbstractDirections}) where {N}
```

Overapproximate a set with template directions.

### Input

  * `X`    – set
  * `dirs` – type of direction representation

### Output

A polyhedron overapproximating the set `X` with the directions from `dirs`. The result is an `HPolytope` if it is bounded and otherwise an `HPolyhedron`.
