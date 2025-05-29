```
V, Ψ, T, U, Φᴴ, Tᴴ = nonhermitian_lanczos(A, B, C, k)
```

#### Input arguments

  * `A`: a linear operator that models a square matrix of dimension `n`;
  * `B`: a matrix of size `n × p`;
  * `C`: a matrix of size `n × p`;
  * `k`: the number of iterations of the block non-Hermitian Lanczos process.

#### Output arguments

  * `V`: a dense `n × p(k+1)` matrix;
  * `Ψ`: a dense `p × p` upper triangular matrix such that `V₁Ψ = B`;
  * `T`: a sparse `p(k+1) × pk` block tridiagonal matrix with a bandwidth `p`;
  * `U`: a dense `n × p(k+1)` matrix;
  * `Φᴴ`: a dense `p × p` upper triangular matrix such that `U₁Φᴴ = C`;
  * `Tᴴ`: a sparse `p(k+1) × pk` block tridiagonal matrix with a bandwidth `p`.
