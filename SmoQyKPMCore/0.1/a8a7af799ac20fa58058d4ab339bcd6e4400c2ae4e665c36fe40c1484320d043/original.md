```
kpm_eval(A::AbstractMatrix{T}, kpm_expansion::KPMExpansion{T}) where {T<:AbstractFloat}
```

Evaluate and return the matrix $F(A),$ where $A$ is an operator with strictly real eigenvalues and the function $F(\bullet)$ is represented by a Chebyshev expansion with coefficients given by the vector `coefs`.
