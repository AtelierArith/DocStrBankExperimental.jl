```
GramSchmidt(S; orthogonalization_interval = 1) <: SpectralStrategy{S}
```

Use the Gram-Schmidt procedure to orthogonalize the excited states. A total of `S` spectral states are used in the simulation, and they are orthogonalized every  `orthogonalization_interval` steps.

Use with the keyword argument `spectral_strategy` in [`ProjectorMonteCarloProblem`](@ref).
