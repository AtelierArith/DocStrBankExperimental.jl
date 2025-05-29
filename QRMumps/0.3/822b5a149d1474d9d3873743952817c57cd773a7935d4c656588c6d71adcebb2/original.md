```
qrm_apply!(spfct, b; transp='n')
```

This routine computes `z = Qb`, `z = Qᵀb` or `z = Qᴴb` in place and overwrites b. It can only be executed once the factorization is done.

#### Input Arguments :

  * `spfct`: the sparse factorization object resulting from the qrm_factorize! function.
  * `b`: the vector(s) to which Q, Qᵀ or Qᴴ is applied.
  * `transp`: whether to apply Q, Qᵀ or Qᴴ. Can be either `'t'`, `'c'` or `'n'`.
