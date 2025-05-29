```
cheb_series_chop(coeffs::AbstractVector{TF}, tol::TF = eps(TF)) where {TF<:AbstractFloat}
```

係数ベクトルに対して「標準」切り捨てルール [aurentz2015choppingchebyshevseries](@cite) を使用して適切なカットオフインデックスを決定します。

# 参考文献

  * [aurentz2015choppingchebyshevseries](@citet*) Aurentz, J. L., & Trefethen, L. N. (2015). チェビシェフ級数の切り捨て. ACM Transactions on Mathematical Software (TOMS), 41(4), 1-18.
  * [chebfun/standardChop.m](https://github.com/chebfun/chebfun/blob/master/%40chebtech/standardChop.m) (Chebfun, MATLABでの実装)
