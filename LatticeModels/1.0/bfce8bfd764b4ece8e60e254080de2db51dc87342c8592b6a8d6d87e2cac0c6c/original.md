```
CachedExp([ham; threshold=1e-10, nztol=1e-14])
```

A `EvolutionSolver` that finds the matrix exponential of the Hamiltonian and caches it. The matrix exponential is computed using a scaling and squaring method, so this solver works well with sparse or GPU arrays.

## Arguments

  * `ham`: The Hamiltonian of the system. It can be an `Operator` or its matrix.
  * `threshold`: The threshold for the error in the matrix exponential.
  * `nztol`: The tolerance for dropping small elements in the matrix exponential if it is   sparse.
