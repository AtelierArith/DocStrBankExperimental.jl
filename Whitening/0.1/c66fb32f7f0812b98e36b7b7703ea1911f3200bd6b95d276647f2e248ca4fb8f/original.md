```
ZCAcor{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

Scale-invariant zero-phase component analysis (ZCA-cor) whitening transform.

Given the correlation matrix, $P$, and the diagonal variance matrix, $V$, we have the whitening matrix, $W = P^{-\frac{1}{2}}V^{-\frac{1}{2}}$.
