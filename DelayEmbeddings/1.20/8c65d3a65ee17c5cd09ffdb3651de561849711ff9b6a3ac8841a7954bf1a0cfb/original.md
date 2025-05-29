```
AbstractNeighborhood
```

Supertype of methods for deciding the neighborhood of points for a given point.

Concrete subtypes:

  * `FixedMassNeighborhood(K::Int)` : The neighborhood of a point consists of the `K` nearest neighbors of the point.
  * `FixedSizeNeighborhood(ε::Real)` : The neighborhood of a point consists of all neighbors that have distance < `ε` from the point.

See [`neighborhood`](@ref) for more.
