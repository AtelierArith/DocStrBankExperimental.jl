```
nystrom(k::Kernel, X::AbstractVector, r::Real)
```

Compute a factorization of a Nystrom approximation of the square kernel matrix of data vector `X` with respect to kernel `k` using a sample ratio of `r`. Returns a `NystromFact` struct which stores a Nystrom factorization satisfying:

$$
\mathbf{K} \approx \mathbf{C}^{\intercal}\mathbf{W}\mathbf{C}
$$
