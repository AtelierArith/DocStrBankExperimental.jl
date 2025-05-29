```
V, β, T, U, γᴴ, Tᴴ = saunders_simon_yip(A, b, c, k; allow_breakdown=false)
```

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `b`: a vector of length `m`;
  * `c`: a vector of length `n`;
  * `k`: the number of iterations of the Saunders-Simon-Yip process.

#### Keyword argument

  * `allow_breakdown`: specify whether to continue the process or raise an error when an exact breakdown occurs.

#### Output arguments

  * `V`: a dense `m × (k+1)` matrix;
  * `β`: a coefficient such that `βv₁ = b`;
  * `T`: a sparse `(k+1) × k` tridiagonal matrix;
  * `U`: a dense `n × (k+1)` matrix;
  * `γᴴ`: a coefficient such that `γᴴu₁ = c`;
  * `Tᴴ`: a sparse `(k+1) × k` tridiagonal matrix.

#### Reference

  * M. A. Saunders, H. D. Simon, and E. L. Yip, [*Two Conjugate-Gradient-Type Methods for Unsymmetric Linear Equations*](https://doi.org/10.1137/0725052), SIAM Journal on Numerical Analysis, 25(4), pp. 927–940, 1988.
