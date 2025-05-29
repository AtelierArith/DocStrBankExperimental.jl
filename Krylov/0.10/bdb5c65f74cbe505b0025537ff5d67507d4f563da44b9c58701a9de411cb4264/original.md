```
V, β, T, U, γᴴ, Tᴴ = nonhermitian_lanczos(A, b, c, k; allow_breakdown=false)
```

#### Input arguments

  * `A`: a linear operator that models a square matrix of dimension `n`;
  * `b`: a vector of length `n`;
  * `c`: a vector of length `n`;
  * `k`: the number of iterations of the non-Hermitian Lanczos process.

#### Keyword argument

  * `allow_breakdown`: specify whether to continue the process or raise an error when an exact breakdown occurs.

#### Output arguments

  * `V`: a dense `n × (k+1)` matrix;
  * `β`: a coefficient such that `βv₁ = b`;
  * `T`: a sparse `(k+1) × k` tridiagonal matrix;
  * `U`: a dense `n × (k+1)` matrix;
  * `γᴴ`: a coefficient such that `γᴴu₁ = c`;
  * `Tᴴ`: a sparse `(k+1) × k` tridiagonal matrix.

#### References

  * C. Lanczos, [*An Iteration Method for the Solution of the Eigenvalue Problem of Linear Differential and Integral Operators*](https://doi.org/10.6028/jres.045.026), Journal of Research of the National Bureau of Standards, 45(4), pp. 225–280, 1950.
  * H. I. van der Veen and K. Vuik, [*Bi-Lanczos with partial orthogonalization*](https://doi.org/10.1016/0045-7949(94)00565-K), Computers & structures, 56(4), pp. 605–613, 1995.
