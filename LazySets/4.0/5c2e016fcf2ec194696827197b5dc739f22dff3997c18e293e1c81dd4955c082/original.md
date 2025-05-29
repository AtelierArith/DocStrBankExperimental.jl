```
ρ(d::AbstractVector, cap::Intersection{N, S1, S2}; kwargs...
 ) where {N, S1<:AbstractPolyhedron, S2<:AbstractPolyhedron}
```

Evaluate the support function of the intersection between two polyhedral sets.

### Input

  * `d`      – direction
  * `cap`    – intersection of two polyhedral sets
  * `kwargs` – additional arguments that are passed to the support-function             algorithm

### Output

The evaluation of the support function in the given direction.

### Algorithm

We combine the constraints of the two polyhedra to a new `HPolyhedron`, for which we then evaluate the support function.
