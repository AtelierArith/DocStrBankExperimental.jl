```
cov_whitening(C)
```

Derive the whitening transform coefficient matrix `W` given the covariance matrix `C`. Here, `C` can be either a square matrix, or an instance of `Cholesky`.

Internally, this function solves the whitening transform using Cholesky factorization. The rationale is as follows: let $\mathbf{C} = \mathbf{U}^T \mathbf{U}$ and $\mathbf{W} = \mathbf{U}^{-1}$, then $\mathbf{W}^T \mathbf{C} \mathbf{W} = \mathbf{I}$.

**Note:** The return matrix `W` is an upper triangular matrix.
