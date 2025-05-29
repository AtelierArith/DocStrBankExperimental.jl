```
minkowski_sum(P::LazySet, Q::LazySet;
              [backend]=nothing, [algorithm]=nothing, [prune]=true)
```

Compute the Minkowski sum of two polyhedral sets.

### Input

  * `P`         – polyhedral set
  * `Q`         – polyhedral set
  * `backend`   – (optional, default: `nothing`) polyhedral computations backend
  * `algorithm` – (optional, default: `nothing`) algorithm to eliminate                variables; available options are `Polyhedra.FourierMotzkin`,                `Polyhedra.BlockElimination`, and `Polyhedra.ProjectGenerators`
  * `prune`     – (optional, default: `true`) if `true`, apply a post-processing                to remove redundant constraints or vertices

### Output

In two dimensions, if the sets are polygons, the result is a `VPolygon`. In higher dimensions, the result is an `HPolytope` if both `P` and `Q` are known to be bounded by their types, and an `HPolyhedron` otherwise.

### Notes

This method requires that the list of constraints of both sets `P` and `Q` can be obtained. After obtaining the respective lists of constraints, the `minkowski_sum` method for polyhedral sets is used.
