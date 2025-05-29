```
abstract type SingleManifoldAlgorithm{M <: Manifold} <: Algorithm{M}
```

The abstract supertype for a single-manifold algorithm, i.e., one which is known to only work  on a single manifold.

The manifold may be accessed via `manifold(alg)`.
