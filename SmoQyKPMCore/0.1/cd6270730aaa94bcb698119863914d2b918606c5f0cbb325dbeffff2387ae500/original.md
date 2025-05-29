```
kpm_eval(A::AbstractMatrix, coefs, bounds)
```

Evaluate and return the matrix $F(A),$ where $A$ is an operator with strictly real eigenvalues that fall in the interval `(bounds[1], bounds[2])` specified by the `bounds` argument, and the function $F(\bullet)$ is represented by a Chebyshev expansion with coefficients given by the vector `coefs`.
