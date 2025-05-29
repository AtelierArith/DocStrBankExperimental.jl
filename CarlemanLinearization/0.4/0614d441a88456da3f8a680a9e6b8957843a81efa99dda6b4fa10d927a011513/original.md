```
build_matrix(F₁, F₂, N; compress=false)
```

Compute the Carleman linearization matrix associated to the quadratic system $x' = F₁x + F₂(x⊗x)$, truncated at order $N$.

### Input

  * `F₁` – sparse matrix of size $n × n$
  * `F₂` – sparse matrix of size $n × n^2$
  * `N`  – integer representing the truncation order, should be at least two
  * `compress` – if `true` produces the matrix corresponding to the commutative monomials only

### Output

Sparse matrix `A`.

### Algorithm

See references [1] and [2] of CARLIN.md.
