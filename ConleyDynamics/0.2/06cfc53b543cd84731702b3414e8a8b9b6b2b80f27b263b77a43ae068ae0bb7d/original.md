```
manifold_boundary(lc::LefschetzComplex)
```

Extract the manifold boundary from a Lefschetz complex.

The function expects a Lefschetz complex which represents a compact d-dimensional manifold with boundary. It returns a  list of all cells which lie on the topological boundary of the manifold, in the form of a `Vector{Int}`.
