Add a column to a QR factorization without using Q.

`R = qraddcol(A,R,v)`  adds the m-vector `v` to the QR factorization of the m-by-n matrix `A` without using `Q`. On entry, `R` is a dense n-by-n upper triangular matrix such that `R'*R = A'*A`.

`R = qraddcol(A,R,v,β)` is similar to the above, except that the routine updates the QR factorization of

```
[A; β I],   and   R'*R = (A'*A + β^2*I).
```

`A` should have fewer columns than rows.  `A` and `v` may be sparse or dense.  On exit, `R` is the (n+1)-by-(n+1) factor corresponding to

```
  Anew = [A        V ],    Rnew = [R   u  ],   Rnew'Rnew = Anew'Anew.
         [beta*I     ]            [  gamma]
         [       beta]
```

The new column `v` is assumed to be nonzero. If `A` has no columns yet, input `A = []`, `R = []`.
