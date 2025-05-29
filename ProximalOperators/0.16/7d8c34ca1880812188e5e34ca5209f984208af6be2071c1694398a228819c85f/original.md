```
LeastSquares(A, b, λ=1.0; iterative=false)
```

For a matrix `A`, a vector `b` and a scalar `λ`, return the function

$$
f(x) = \tfrac{\lambda}{2}\|Ax - b\|^2.
$$

By default, a direct method (based on Cholesky factorization) is used to evaluate `prox!`. If `iterative=true`, then `prox!` is evaluated approximately using an iterative method instead.
