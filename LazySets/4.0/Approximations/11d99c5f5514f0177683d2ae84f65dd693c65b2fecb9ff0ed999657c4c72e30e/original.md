```
overapproximate(cap::Intersection{N, <:LazySet, <:AbstractPolyhedron},
                dirs::AbstractDirections;
                kwargs...
               ) where {N}
```

Overapproximate the intersection between a set and a polyhedron given a set of template directions.

### Input

  * `cap`    – intersection of a set and a polyhedron
  * `dirs`   – template directions
  * `kwargs` – additional arguments that are passed to the support function             algorithm

### Output

A polytope or polyhedron in H-representation such that the normal direction of each half-space is given by an element of `dirs`.

### Algorithm

Let `di` be a direction drawn from the set of template directions `dirs`. Let `X` be the set and let `P` be the polyhedron. We overapproximate the set `X ∩ H` with a polytope or polyhedron in constraint representation using a given set of template directions `dirs`.

The idea is to solve the univariate optimization problem `ρ(di, X ∩ Hi)` for each half-space of the set `P` and then take the minimum. This gives an overapproximation of the exact support function.

This algorithm is inspired from [Frehse012](@citet).

### Notes

This method relies on having available the `constraints_list` of the polyhedron `P`.

This method may return a non-empty set even if the original set is empty.
