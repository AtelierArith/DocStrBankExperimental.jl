```
exp_and_gram(
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AbstractExpAndGramAlgorithm,
)
```

Compute the matrix exponential exp(A) and the controllability Gramian of (A, B) over the interval [0, t], if t is omitted the unit interval is used.
