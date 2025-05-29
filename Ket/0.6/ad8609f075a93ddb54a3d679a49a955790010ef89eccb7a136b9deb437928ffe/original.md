```
relative_entropy([base=2,] ρ::AbstractMatrix, σ::AbstractMatrix)
```

Computes the (quantum) relative entropy tr(`ρ` (log `ρ` - log `σ`)) between positive semidefinite matrices `ρ` and `σ` using a base `base` logarithm. Note that the support of `ρ` must be contained in the support of `σ` but for efficiency this is not checked.

Reference: [Quantum relative entropy](https://en.wikipedia.org/wiki/Quantum_relative_entropy)
