```
convex_hull(P1::VPolytope, P2::VPolytope; [backend]=nothing)
```

Compute the convex hull of two polytopes in vertex representation.

### Input

  * `P1`      – polytope in vertex representation
  * `P2`      – polytope in vertex representation
  * `backend` – (optional, default: `nothing`) the polyhedral computation backend

### Output

The `VPolytope` obtained by the concrete convex hull of `P1` and `P2`.

### Notes

This function takes the union of the vertices of each polytope and then relies on a concrete convex-hull algorithm. For low dimensions, a specialized implementation for polygons is used. For higher dimensions, `convex_hull` relies on the polyhedral backend that can be specified using the `backend` keyword argument.

For performance reasons, it is suggested to use the `CDDLib.Library()` backend.
