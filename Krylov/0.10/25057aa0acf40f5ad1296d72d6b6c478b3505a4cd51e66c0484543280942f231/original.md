```
V, Ψ, T, U, Φᴴ, Tᴴ = saunders_simon_yip(A, B, C, k; algo="householder")
```

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `B`: a matrix of size `m × p`;
  * `C`: a matrix of size `n × p`;
  * `k`: the number of iterations of the block Saunders-Simon-Yip process.

#### Keyword argument

  * `algo`: the algorithm to perform reduced QR factorizations (`"gs"`, `"mgs"`, `"givens"` or `"householder"`).

#### Output arguments

  * `V`: a dense `m × p(k+1)` matrix;
  * `Ψ`: a dense `p × p` upper triangular matrix such that `V₁Ψ = B`;
  * `T`: a sparse `p(k+1) × pk` block tridiagonal matrix with a bandwidth `p`;
  * `U`: a dense `n × p(k+1)` matrix;
  * `Φᴴ`: a dense `p × p` upper triangular matrix such that `U₁Φᴴ = C`;
  * `Tᴴ`: a sparse `p(k+1) × pk` block tridiagonal matrix with a bandwidth `p`.
