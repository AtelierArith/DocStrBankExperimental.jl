```
qrm_factorize!(spmat, spfct; transp='n')
```

This routine performs the factorization phase. It can only be executed if the analysis is already done.

#### Input Arguments :

  * `spmat`: the input matrix of type `qrm_spmat`.
  * `spfct`: the sparse factorization object of type `qrm_spfct`.
  * `transp`: whether the input matrix should be transposed or not. Can be either `'t'`, `'c'` or `'n'`.
