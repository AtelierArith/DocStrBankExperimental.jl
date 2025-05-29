```
d = solve_linlsqr!(A, b, linlsqr, droptol)
```

Solves the linear least squares problem

```
Ad=b.
```

The argument `linlsqr` determines how the linear least squares problem is solved. It can be `:backslash`, `:real_backslash`, `:nrmeq`, `:real_nrmeq`, `:svd`, or `:real_svd`. For the latter two options singular values below `droptol` are disregarded. The `:real_X` options optimizes `d` in the space of real vectors. The input matrix `A` is sometimes overwritten.
