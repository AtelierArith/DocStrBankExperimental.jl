```
exp_and_gram_chol(
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AbstractExpAndGramAlgorithm,
)
```

Computes the matrix exponential of A * t and the controllability Gramian of (A, B) on the interval [0, t], if t is omitted the unit interval is used.
