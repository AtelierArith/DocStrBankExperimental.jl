```
Quadratic(Q, q; iterative=false)
```

For a matrix `Q` (dense or sparse, symmetric and positive semidefinite) and a vector `q`, return the quadratic function

$$
f(x) = \tfrac{1}{2}\langle Qx, x\rangle + \langle q, x \rangle.
$$

By default, a direct method (based on Cholesky factorization) is used to evaluate `prox!`. If `iterative=true`, then `prox!` is evaluated approximately using an iterative method instead.
