```
vertices_list(P::HPolytope; [backend]=nothing, [prune]::Bool=true)
```

Return a list of the vertices of a polytope in constraint representation.

### Input

  * `P`       – polytope in constraint representation
  * `backend` – (optional, default: `nothing`) the backend for polyhedral              computations
  * `prune`   – (optional, default: `true`) flag to remove redundant vertices

### Output

A list of the vertices.

### Algorithm

If the polytope is one-dimensional (resp. two-dimensional), it is converted to an interval (resp. polygon in constraint representation) and then the respective optimized `vertices_list` implementation is used.

It is possible to use the `Polyhedra` backend in the one- and two-dimensional case as well by passing a `backend`.

If the polytope is not two-dimensional, the concrete polyhedra-manipulation library `Polyhedra` is used. The actual computation is performed by a given backend; for the default backend used in `LazySets` see `default_polyhedra_backend(P)`. For further information on the supported backends see [Polyhedra's documentation](https://juliapolyhedra.github.io/Polyhedra.jl/).
