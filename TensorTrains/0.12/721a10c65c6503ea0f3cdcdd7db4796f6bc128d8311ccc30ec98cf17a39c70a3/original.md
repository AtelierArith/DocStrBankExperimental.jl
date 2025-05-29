```
TruncBondMax{T} <: SVDTrunc
```

Similar to [`TruncBond`](@ref), but also stores the maximum error $\sqrt{\frac{\sum_{k=m'+1}^m\lambda_k^2}{\sum_{k=1}^m\lambda_k^2}}$ made since the creation of the object

# FIELDS

  * `mprime`: number of singular values to retain
  * `maxerr`: a 1-element vector storing the maximum error
