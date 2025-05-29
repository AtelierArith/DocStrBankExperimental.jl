# Extended help

```
isempty(P::LazySet, witness::Bool=false;
        [use_polyhedra_interface]::Bool=false, [solver]=nothing,
        [backend]=nothing)
```

### Input

  * `witness` – (optional, default: `false`) compute a witness if activated
  * `use_polyhedra_interface` – (optional, default: `false`) if `true`, we use              the `Polyhedra` interface for the emptiness test
  * `solver`  – (optional, default: `nothing`) LP-solver backend; uses              `default_lp_solver` if not provided
  * `backend` – (optional, default: `nothing`) backend for polyhedral              computations in `Polyhedra`; uses `default_polyhedra_backend(P)`              if not provided

### Notes

This implementation assumes that `P` is polyhedral.

The default value of the `backend` is set internally and depends on whether the `use_polyhedra_interface` option is set. If the option is set, we use `default_polyhedra_backend(P)`.

Witness production is not supported if `use_polyhedra_interface` is `true`.

### Algorithm

The algorithm sets up a feasibility LP for the constraints of `P`. If `use_polyhedra_interface` is `true`, we call `Polyhedra.isempty`. Otherwise, we set up the LP internally.
