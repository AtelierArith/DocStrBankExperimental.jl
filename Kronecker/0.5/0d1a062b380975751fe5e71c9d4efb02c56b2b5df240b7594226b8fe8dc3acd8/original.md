```
lmul!(a::Number, K::KroneckerPower)
```

Scale an `KroneckerPower` `K` inplace by a factor `a` by rescaling the matrix the base matrix with a factor `a^(1/N)`.

It is recommended to rewrite your Kronecker product rather as `copy(A) ⊗ (A ⊗ n - 1)` (note the copy) for numerical stability. This will only modify the first matrix, leaving the chain of Kronecker products alone.
