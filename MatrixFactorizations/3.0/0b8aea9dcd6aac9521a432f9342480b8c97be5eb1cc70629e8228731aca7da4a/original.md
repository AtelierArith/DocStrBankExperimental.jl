```
PolarDecomposition <: Factorization
```

Matrix factorization type of the polar decomposition of a matrix $A$. This is the return type of [`polar(_)`](@ref), the corresponding matrix factorization function.

Every $m-by-n$ matrix $A$ has a polar decomposition

$$
A = U H
$$

where the $m-by-n$ matrix $U$ has orthonormal columns if $m>n$ or orthonormal rows if $m<n$ and the $n-by-n$ matrix $H$ is Hermitian positive semidefinite. For a square matrix $A$, $H$ is unique. If in addition, $A$ is nonsingular, then $H$ is positive definite and $U$ is unique.

Iterating the decomposition produces the components $U$ and $H$.
