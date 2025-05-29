```
cheb_series_chop(coeffs::AbstractVector{TF}, tol::TF = eps(TF)) where {TF<:AbstractFloat}
```

Determine a suitable cutoff index for a coefficient vector using the "standard" chopping rule [aurentz2015choppingchebyshevseries](@cite).

# References

  * [aurentz2015choppingchebyshevseries](@citet*) Aurentz, J. L., & Trefethen, L. N. (2015). Chopping a Chebyshev series. ACM Transactions on Mathematical Software (TOMS), 41(4), 1-18.
  * [chebfun/standardChop.m](https://github.com/chebfun/chebfun/blob/master/%40chebtech/standardChop.m) (Implementation in Chebfun, MATLAB)
