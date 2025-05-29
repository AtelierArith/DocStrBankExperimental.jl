```
schmidt_decomposition(ψ::AbstractVector, dims::AbstractVecOrTuple = _equal_sizes(ψ))
```

Produces the Schmidt decomposition of `ψ` with subsystem dimensions `dims`. If the argument `dims` is omitted equally-sized subsystems are assumed. Returns the (sorted) Schmidt coefficients λ and isometries U, V such that kron(U', V')*`ψ` is of Schmidt form.

Reference: [Schmidt decomposition](https://en.wikipedia.org/wiki/Schmidt_decomposition)
