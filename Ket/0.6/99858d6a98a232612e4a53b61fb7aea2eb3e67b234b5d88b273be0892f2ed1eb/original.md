```
conditional_entropy([base=2,], rho::AbstractMatrix, csys::AbstractVecOrTuple, dims::AbstractVecOrTuple)
```

Computes the conditional von Neumann entropy of `rho` with subsystem dimensions `dims` and conditioning systems `csys`, using a base `base` logarithm.

Reference: [Conditional quantum entropy](https://en.wikipedia.org/wiki/Conditional_quantum_entropy)
