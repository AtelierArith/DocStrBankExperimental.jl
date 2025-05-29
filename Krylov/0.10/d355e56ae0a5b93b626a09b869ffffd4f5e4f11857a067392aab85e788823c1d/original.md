```
V, β, H = arnoldi(A, b, k; allow_breakdown=false, reorthogonalization=false)
```

#### Input arguments

  * `A`: a linear operator that models a square matrix of dimension `n`;
  * `b`: a vector of length `n`;
  * `k`: the number of iterations of the Arnoldi process.

#### Keyword arguments

  * `allow_breakdown`: specify whether to continue the process or raise an error when an exact breakdown occurs;
  * `reorthogonalization`: reorthogonalize each newly added vector of the Krylov basis against all previous vectors (full reorthogonalization).

#### Output arguments

  * `V`: a dense `n × (k+1)` matrix;
  * `β`: a coefficient such that `βv₁ = b`;
  * `H`: a dense `(k+1) × k` upper Hessenberg matrix.

#### Reference

  * W. E. Arnoldi, [*The principle of minimized iterations in the solution of the matrix eigenvalue problem*](https://doi.org/10.1090/qam/42792), Quarterly of Applied Mathematics, 9, pp. 17–29, 1951.
