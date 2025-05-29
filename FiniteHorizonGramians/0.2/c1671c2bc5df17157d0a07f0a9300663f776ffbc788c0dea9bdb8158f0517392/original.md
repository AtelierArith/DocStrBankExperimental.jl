```
exp_and_gram!(
    eA::AbstractMatrix{T},
    G::AbstractMatrix{T},
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AbstractExpAndGramAlgorithm,
    cache = alloc_mem(A, B, method),
)
```

Computes the matrix exponential of A * t and the controllability Gramian of (A, B) on the interval [0, t], if t is omitted the unit interval is used. The result is stored in (eA, G), which are returned.
