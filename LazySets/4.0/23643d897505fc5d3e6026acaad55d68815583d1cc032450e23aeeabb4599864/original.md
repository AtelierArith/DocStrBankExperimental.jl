```
intersection(P1::AbstractPolyhedron{N}, P2::AbstractPolyhedron{N};
             [backend]=default_lp_solver(N), [prune]::Bool=true) where {N}
```

Compute the intersection of two polyhedra.

### Input

  * `P1`      – polyhedron
  * `P2`      – polyhedron
  * `backend` – (optional, default: `default_lp_solver(N)`) the LP solver used              for the removal of redundant constraints; see the *Notes* section              below for details
  * `prune`   – (optional, default: `true`) flag for removing redundant              constraints

### Output

An `HPolyhedron` resulting from the intersection of `P1` and `P2`, with the redundant constraints removed, or an empty set if the intersection is empty. If one of the arguments is a polytope, the result is an `HPolytope` instead.

### Notes

The default value of the solver backend is `default_lp_solver(N)` and it is used to run a feasiblity LP to remove the redundant constraints of the intersection.

If you want to use the `Polyhedra` library, pass an appropriate backend. For example, use `default_polyhedra_backend(P)` for the default Polyhedra library, or use `CDDLib.Library()` for the CDD library.

There are some shortcomings of the removal of constraints using the default Polyhedra library; see e.g. #1038 and Polyhedra#146. It is safer to check for emptiness of intersection before calling this function in those cases.

### Algorithm

This implementation unifies the constraints of the two sets obtained from the `constraints_list` method.
