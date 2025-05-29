```
ZCA{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Zero-phase component analysis (ZCA) whitening transform.

Given the covariance matrix, $Σ$, we have the whitening matrix, $W = Σ^{-\frac{1}{2}}$.
