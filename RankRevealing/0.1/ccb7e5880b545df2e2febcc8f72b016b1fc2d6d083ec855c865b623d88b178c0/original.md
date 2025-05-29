```
pluq(A) -> PLUQ
```

Perform a rank-sensitive LU factorization of `A`. The factorization of an `n` by `m` matrix is computed in `O(n m r^(ω-2))` steps, where `r = rank(A)` and `ω` is the matrix multiplication complexity exponent.

This is an exact function who should work with any type implementing the basic arithmetic operations `+`, `-`, `*`, `/`, `one`, `zero`.

The resulting factorization `F` satisfies

```
F.P * [F.L ; F.M] * [F.U F.V] * F.Q == A
```

See [the link](https://arxiv.org/pdf/1301.4438.pdf) for the original description of the algorithm.
