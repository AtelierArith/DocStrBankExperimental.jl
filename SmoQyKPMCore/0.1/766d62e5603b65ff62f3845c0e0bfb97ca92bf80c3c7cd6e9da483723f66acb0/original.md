```
kpm_eval!(
    F::AbstractMatrix, A, kpm_expansion::KPMExpansion,
    tmp = zeros(eltype(F), size(F)..., 3)
)
```

Evaluate and write the matrix $F(A)$ to `F`, where $A$ is an operator with strictly real eigenvalues and the function $F(\bullet)$ is represented by a Chebyshev expansion with coefficients given by the vector `coefs`. Lastly, the array `tmp` is used to avoid dynamic memory allocations.
