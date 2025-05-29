# Extended help

```
volume(P::AbstractPolytope; backend=default_polyhedra_backend(P))
```

### Input

  * `backend` – (optional, default: `default_polyhedra_backend(P)`) the backend              for polyhedral computations; see [Polyhedra's              documentation](https://juliapolyhedra.github.io/) for further              information

### Algorithm

The volume is computed by the `Polyhedra` library.
