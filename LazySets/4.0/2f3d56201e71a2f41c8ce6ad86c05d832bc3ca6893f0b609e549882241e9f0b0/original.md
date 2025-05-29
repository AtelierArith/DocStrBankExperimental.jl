```
cartesian_product(X::LazySet, Y::LazySet; [backend]=nothing,
                  [algorithm]::String="vrep")
```

Compute the Cartesian product of two sets.

### Input

  * `X`         – set
  * `Y`         – set
  * `backend`   – (optional, default: `nothing`) backend for polyhedral                computation
  * `algorithm` – (optional, default: "hrep") the method used to transform the                sets `X` and `Y` before taking the Cartesian product; choose                between:

      * "vrep" (use the vertex representation)
      * "hrep" (use the constraint representation)
      * "hrep_polyhedra" (use the constraint representation and `Polyhedra`)

### Output

The `VPolytope` (if `"vrep"` was used) or `HPolytope`/`HPolyhedron` (if `"hrep"` or `"hrep_polyhedra"` was used) obtained by the concrete Cartesian product of `X` and `Y`. The choice between `HPolytope` and `HPolyhedron` is made based on boundedness information deduced from the type.

### Notes

For further information on the supported backends see [Polyhedra's documentation](https://juliapolyhedra.github.io/).

If `X` can be converted to a one-dimensional interval and the vertices of `Y` are available, use `algorithm="vrep"`.
