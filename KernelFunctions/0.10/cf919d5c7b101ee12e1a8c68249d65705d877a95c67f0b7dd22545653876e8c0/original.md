```
nystrom(k::Kernel, X::AbstractVector, S::AbstractVector{<:Integer})
```

Compute a factorization of a Nystrom approximation of the square kernel matrix of data vector `X` with respect to kernel `k`, using indices `S`. Returns a `NystromFact` struct which stores a Nystrom factorization satisfying:

$$
\mathbf{K} \approx \mathbf{C}^{\intercal}\mathbf{W}\mathbf{C}
$$
