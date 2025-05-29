```
qrm_analyse!(spmat, spfct; transp='n')
```

This routine performs the analysis phase and updates spfct.

#### Input Arguments :

  * `spmat`: the input matrix of type `qrm_spmat`.
  * `spfct`: the sparse factorization object of type `qrm_spfct`.
  * `transp`: whether the input matrix should be transposed or not. Can be either `'t'`, `'c'` or `'n'`.
