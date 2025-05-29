```
solve(A, rhs; sym=mumps_unsymmetric)
```

Combined initialize / analyze / factorize / solve. Presume that `A` and `rhs` are available on all nodes. The optional keyword argument `sym` indicates the symmetry of `A`. The solution is retrieved and returned.
