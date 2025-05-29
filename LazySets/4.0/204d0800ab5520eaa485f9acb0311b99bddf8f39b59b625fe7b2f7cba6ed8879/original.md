```
ρ(d::AbstractVector, cap::Intersection{N, S1, S2};
  kwargs...) where {N, S1<:LazySet, S2<:AbstractPolyhedron}
```

Return an upper bound on the support function of the intersection between a compact set and a polyhedron along a given direction.

### Input

  * `d`      – direction
  * `cap`    – intersection of a compact set and a polyhedron
  * `kwargs` – additional arguments that are passed to the support-function             algorithm

### Output

An upper bound of the support function of the given intersection.

### Algorithm

The idea is to solve the univariate optimization problem `ρ(di, X ∩ Hi)` for each half-space in the polyhedron and then take the minimum. This gives an overapproximation of the exact support value.

This algorithm is inspired from [Frehse012](@citet).

### Notes

This method relies on the `constraints_list` of the polyhedron.
