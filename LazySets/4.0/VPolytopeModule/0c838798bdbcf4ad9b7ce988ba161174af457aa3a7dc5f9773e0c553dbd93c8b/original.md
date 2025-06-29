```
tohrep(P::VPolytope; [backend]=default_polyhedra_backend(P))
```

Transform a polytope in vertex representation to a polytope in constraint representation.

### Input

  * `P`       – polytope in vertex representation
  * `backend` – (optional, default: `default_polyhedra_backend(P)`) the              backend for polyhedral computations; see [Polyhedra's              documentation](https://juliapolyhedra.github.io/) for further              information

### Output

A `HPolytope` as the constraint representation of `P`.

### Notes

The conversion may not preserve the numeric type (e.g., with `N == Float32`) depending on the backend.
