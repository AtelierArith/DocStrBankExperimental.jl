```
V, U, Ψ, L = golub_kahan(A, B, k; algo="householder")
```

#### Input arguments

  * `A`: a linear operator that models a matrix of dimension `m × n`;
  * `B`: a matrix of size `m × p`;
  * `k`: the number of iterations of the block Golub-Kahan process.

#### Keyword argument

  * `algo`: the algorithm to perform reduced QR factorizations (`"gs"`, `"mgs"`, `"givens"` or `"householder"`).

#### Output arguments

  * `V`: a dense `n × p(k+1)` matrix;
  * `U`: a dense `m × p(k+1)` matrix;
  * `Ψ`: a dense `p × p` upper triangular matrix such that `U₁Ψ = B`;
  * `L`: a sparse `p(k+1) × p(k+1)` block lower bidiagonal matrix with a lower bandwidth `p`.
