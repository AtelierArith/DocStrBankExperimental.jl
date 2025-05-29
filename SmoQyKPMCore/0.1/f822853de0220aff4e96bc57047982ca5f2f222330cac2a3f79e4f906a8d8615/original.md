```
kpm_eval!(
    F::AbstractMatrix, A, coefs::AbstractVector, bounds,
    tmp = zeros(eltype(F), size(F)..., 4)
)
```

Evaluate and write the matrix $F(A)$ to `F`, where $A$ is an operator with strictly real eigenvalues that fall in the interval `(bounds[1], bounds[2])` specified by the `bounds` argument, and the function $F(\bullet)$ is represented by a Chebyshev expansion with coefficients given by the vector `coefs`. Lastly, `tmp` is used to avoid dynamic memory allocations.
