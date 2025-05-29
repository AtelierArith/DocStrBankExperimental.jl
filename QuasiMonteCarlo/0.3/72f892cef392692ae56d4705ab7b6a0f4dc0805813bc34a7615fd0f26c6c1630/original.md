```
GridSample(R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

A simple rectangular grid lattice. Samples `n` random samples from a grid with `dx = (ub -lb)/n``

In more than 2 dimensions, grids have worse discrepancy than simple Monte Carlo. As a result, they should almost never be used for multivariate integration; their use is as a starting point for other algorithms.
