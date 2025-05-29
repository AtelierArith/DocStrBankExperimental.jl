```
V, β, T = hermitian_lanczos(A, b, k; allow_breakdown=false, reorthogonalization=false)
```

#### Input arguments

  * `A`: a linear operator that models a Hermitian matrix of dimension `n`;
  * `b`: a vector of length `n`;
  * `k`: the number of iterations of the Hermitian Lanczos process.

#### Keyword arguments

  * `allow_breakdown`: specify whether to continue the process or raise an error when an exact breakdown occurs;
  * `reorthogonalization`: reorthogonalize each newly added vector of the Krylov basis against only the two previous vectors (local reorthogonalization).

#### Output arguments

  * `V`: a dense `n × (k+1)` matrix;
  * `β`: a coefficient such that `βv₁ = b`;
  * `T`: a sparse `(k+1) × k` tridiagonal matrix.

#### References

  * C. Lanczos, [*An Iteration Method for the Solution of the Eigenvalue Problem of Linear Differential and Integral Operators*](https://doi.org/10.6028/jres.045.026), Journal of Research of the National Bureau of Standards, 45(4), pp. 225–280, 1950.
  * H. D. Simon, [*The Lanczos algorithm with partial reorthogonalization*](https://doi.org/10.1090/S0025-5718-1984-0725988-X), Mathematics of computation, 42(165), pp. 115–142, 1984.
