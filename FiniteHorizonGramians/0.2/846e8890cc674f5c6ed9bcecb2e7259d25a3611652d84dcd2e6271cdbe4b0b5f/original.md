```
exp_and_gram_chol!(
    eA::AbstractMatrix{T},
    U::AbstractMatrix{T},
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::ExpAndGram{T,q},
    [cache = alloc_mem(A, B, method)],
)

exp_and_gram_chol!(
    eA::AbstractMatrix{T},
    U::AbstractMatrix{T},
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AdaptiveExpAndGram,
    [cache = nothing],
)
```

Computes the matrix exponential of A * t and the controllability Gramian of (A, B) on the interval [0, t], if t is omitted the unit interval is used. The result is stored in (eA, U), which are returned.
