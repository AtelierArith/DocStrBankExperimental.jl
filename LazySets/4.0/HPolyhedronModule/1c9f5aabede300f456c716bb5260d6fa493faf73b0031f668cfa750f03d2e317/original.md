```
convex_hull(P1::HPoly, P2::HPoly;
           [backend]=default_polyhedra_backend(P1))
```

Compute the convex hull of the set union of two polyhedra in constraint representation.

### Input

  * `P1`      – polyhedron
  * `P2`      – polyhedron
  * `backend` – (optional, default: `default_polyhedra_backend(P1)`) the              backend for polyhedral computations

### Output

The `HPolyhedron` (resp. `HPolytope`) obtained by the concrete convex hull of `P1` and `P2`.

### Notes

For performance reasons, it is suggested to use the `CDDLib.Library()` backend for the `convex_hull`.

For further information on the supported backends see [Polyhedra's documentation](https://juliapolyhedra.github.io/).
