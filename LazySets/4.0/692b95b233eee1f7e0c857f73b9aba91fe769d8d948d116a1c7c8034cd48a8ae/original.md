```
HPolygonOpt{N, VN<:AbstractVector{N}} <: AbstractHPolygon{N}
```

Type that represents a convex polygon in constraint representation whose edges are sorted in counter-clockwise fashion with respect to their normal directions. This implementation is a refined version of [`HPolygon`](@ref).

### Fields

  * `constraints` – list of linear constraints, sorted by the normal direction in                  counter-clockwise fashion
  * `ind`         – index in the list of constraints to begin the search to                  evaluate the support vector/function

### Notes

Further constructor arguments:

  * `sort_constraints`  – (optional, default: `true`) flag for sorting the                        constraints (being sorted is a running assumption of                        this type)
  * `check_boundedness` – (optional, default: `false`) flag for checking if the                        constraints make the polygon bounded; (boundedness is a                        running assumption of this type)
  * `prune`             – (optional, default: `true`) flag for removing redundant                        constraints

This structure is optimized to evaluate the support vector/function with a large sequence of directions that are close to each other. The strategy is to have an index that can be used to warm-start the search for optimal values in the support-vector computation.

The option `sort_constraints` can be used to deactivate automatic sorting of constraints in counter-clockwise fashion, which is an invariant of this type. Alternatively, one can construct an `HPolygonOpt` with empty constraints list, which can then be filled iteratively using `addconstraint!`.

Similarly, the option `prune` can be used to deactivate automatic pruning of redundant constraints.

Another type assumption is that the polygon is bounded. The option `check_boundedness` can be used to assert this. This option is deactivated by default because we explicitly want to allow the iterative addition of the constraints, and hence one has to initially construct an empty list of constraints (which represents an unbounded set). The user has to make sure that the `HPolygonOpt` is not used before the constraints actually describe a bounded set.
