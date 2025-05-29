```
V, Γ, H = arnoldi(A, B, k; algo="householder", reorthogonalization=false)
```

#### Input arguments

  * `A`: a linear operator that models a square matrix of dimension `n`;
  * `B`: a matrix of size `n × p`;
  * `k`: the number of iterations of the block Arnoldi process.

#### Keyword arguments

  * `algo`: the algorithm to perform reduced QR factorizations (`"gs"`, `"mgs"`, `"givens"` or `"householder"`).
  * `reorthogonalization`: reorthogonalize each newly added matrix of the block Krylov basis against all previous matrices (full reorthogonalization).

#### Output arguments

  * `V`: a dense `n × p(k+1)` matrix;
  * `Γ`: a dense `p × p` upper triangular matrix such that `V₁Γ = B`;
  * `H`: a dense `p(k+1) × pk` block upper Hessenberg matrix with a lower bandwidth `p`.
