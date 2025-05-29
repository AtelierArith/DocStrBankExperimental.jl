```
CPD
```

Tensor decomposition type for the canonical polyadic decompositions (CPD) of a tensor (i.e., a multi-dimensional array) `A`. This is the return type of `gcp(_)`, the corresponding tensor decomposition function.

If `M::CPD` is the decomposition object, the weights `λ` and the factor matrices `U = (U[1],...,U[N])` can be obtained via `M.λ` and `M.U`, such that `A = Σ_j λ[j] U[1][:,j] ∘ ⋯ ∘ U[N][:,j]`.
