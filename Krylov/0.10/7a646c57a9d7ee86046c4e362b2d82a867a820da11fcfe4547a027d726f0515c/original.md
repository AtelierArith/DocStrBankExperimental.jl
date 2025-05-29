```
V, Ψ, T = hermitian_lanczos(A, B, k; algo="householder")
```

#### Input arguments

  * `A`: a linear operator that models a Hermitian matrix of dimension `n`;
  * `B`: a matrix of size `n × p`;
  * `k`: the number of iterations of the block Hermitian Lanczos process.

#### Keyword arguments

  * `algo`: the algorithm to perform reduced QR factorizations (`"gs"`, `"mgs"`, `"givens"` or `"householder"`).

#### Output arguments

  * `V`: a dense `n × p(k+1)` matrix;
  * `Ψ`: a dense `p × p` upper triangular matrix such that `V₁Ψ = B`;
  * `T`: a sparse `p(k+1) × pk` block tridiagonal matrix with a bandwidth `p`.
