```
tohrep(P::LazySet)
```

Convert a polyhedral set to constraint representation.

### Input

  * `P` – polyhedral set

### Output

An `HPolyhedron` if `P` is bounded (via `isboundedtype`) or an `HPolytope` otherwise.
