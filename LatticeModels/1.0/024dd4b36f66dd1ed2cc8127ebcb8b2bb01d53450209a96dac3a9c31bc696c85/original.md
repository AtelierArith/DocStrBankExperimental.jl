```
KrylovKitExp([ham; kw...])
```

A `EvolutionSolver` that uses the `exponentiate` function from KrylovKit.jl to evolve the wavefunction vectors. This solver is useful for large, sparse, time-dependent Hamiltonians.

## Arguments

  * `ham`: The Hamiltonian of the system. It can be an `Operator` or its matrix.
  * `kw...`: Keyword arguments to be passed to `exponentiate`.
