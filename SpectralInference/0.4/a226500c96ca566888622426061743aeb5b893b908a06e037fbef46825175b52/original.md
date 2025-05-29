```
getintervals_IQR(S::AbstractVector{<:Number}; alpha=1.5, ql=.25, qh=.75)
```

finds spectral partitions. Computes log difference between each subsequent singular value and by default selects the differences that are larger than `1.5 * IQR(differences)`

i.e. finds breaks in the spectrum that explain smaller scales of variance

Args:

  * S: singular values of a SVD factorization
  * alpha: scalar multiple of `q`
  * q: which quantile of log differences to use; by default Q3

Returns:

  * AbstractVector{UnitRange} indices into S corresponding to the spectral partitions
