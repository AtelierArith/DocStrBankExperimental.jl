```
V, β, H, U, γ, F = montoison_orban(A, B, b, c, k; allow_breakdown=false, reorthogonalization=false)
```

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `B`: a linear operator that models a matrix of dimension `n × m`;
  * `b`: a vector of length `m`;
  * `c`: a vector of length `n`;
  * `k`: the number of iterations of the Montoison-Orban process.

#### Keyword arguments

  * `allow_breakdown`: specify whether to continue the process or raise an error when an exact breakdown occurs;
  * `reorthogonalization`: reorthogonalize each newly added vector of the Krylov basis against all previous vectors (full reorthogonalization).

#### Output arguments

  * `V`: a dense `m × (k+1)` matrix;
  * `β`: a coefficient such that `βv₁ = b`;
  * `H`: a dense `(k+1) × k` upper Hessenberg matrix;
  * `U`: a dense `n × (k+1)` matrix;
  * `γ`: a coefficient such that `γu₁ = c`;
  * `F`: a dense `(k+1) × k` upper Hessenberg matrix.

#### Reference

  * A. Montoison and D. Orban, [*GPMR: An Iterative Method for Unsymmetric Partitioned Linear Systems*](https://doi.org/10.1137/21M1459265), SIAM Journal on Matrix Analysis and Applications, 44(1), pp. 293–311, 2023.
