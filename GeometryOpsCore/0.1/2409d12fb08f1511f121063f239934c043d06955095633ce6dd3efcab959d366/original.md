```
abstract type ManifoldIndependentAlgorithm{M <: Manifold} <: Algorithm{M}
```

The abstract supertype for a manifold-independent algorithm, i.e., one which may work on any manifold.

The manifold is stored in the algorithm for a `ManifoldIndependentAlgorithm`, and accessed via `manifold(alg)`.
