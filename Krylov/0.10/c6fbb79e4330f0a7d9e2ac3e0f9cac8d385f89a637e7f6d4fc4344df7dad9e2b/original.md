```
V, U, β, L = golub_kahan(A, b, k; allow_breakdown=false)
```

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`;
  * `k`: the number of iterations of the Golub-Kahan process.

#### Keyword argument

  * `allow_breakdown`: specify whether to continue the process or raise an error when an exact breakdown occurs.

#### Output arguments

  * `V`: a dense `n × (k+1)` matrix;
  * `U`: a dense `m × (k+1)` matrix;
  * `β`: a coefficient such that `βu₁ = b`;
  * `L`: a sparse `(k+1) × (k+1)` lower bidiagonal matrix.

#### References

  * G. H. Golub and W. Kahan, [*Calculating the Singular Values and Pseudo-Inverse of a Matrix*](https://doi.org/10.1137/0702016), SIAM Journal on Numerical Analysis, 2(2), pp. 225–224, 1965.
  * C. C. Paige, [*Bidiagonalization of Matrices and Solution of Linear Equations*](https://doi.org/10.1137/0711019), SIAM Journal on Numerical Analysis, 11(1), pp. 197–209, 1974.
