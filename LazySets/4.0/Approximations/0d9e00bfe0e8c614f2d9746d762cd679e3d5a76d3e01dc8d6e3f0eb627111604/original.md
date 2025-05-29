```
overapproximate(cap::Intersection{N, <:HalfSpace, <:AbstractPolytope},
                dirs::AbstractDirections;
                [kwargs]...
               ) where {N}
```

Overapproximate the intersection between a half-space and a polytope given a set of template directions.

### Input

  * `cap`    – intersection of a half-space and a polytope
  * `dirs`   – template directions
  * `kwargs` – additional arguments that are passed to the support function             algorithm

### Output

A polytope in H-representation such that the normal direction of each half-space is given by an element of `dirs`.
