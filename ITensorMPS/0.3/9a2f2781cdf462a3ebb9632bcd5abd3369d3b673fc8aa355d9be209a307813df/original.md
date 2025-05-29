```
sample(M::MPO)
```

Given a normalized MPO `M`, returns a `Vector{Int}` of `length(M)` corresponding to one sample of the probability distribution defined by the MPO, treating the MPO as a density matrix.

The MPO `M` should have an (approximately) positive spectrum.
