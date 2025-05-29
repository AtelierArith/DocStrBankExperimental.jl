```
struct LegendreFourPiNorm <: AbstractLegendreNorm end
```

Trait type denoting the $4\pi$ (geodesy) normalization of the associated Legendre functions $F_\ell^m(x)$. The orthonormal normalization is defined such that

$$
    \int_{-1}^{1} \left[ F_\ell^m(x) \right]^2 \,dx = 2
$$

The normalization factor with respect to the standard (unnormalized) Legendre functions $P_\ell^m(x)$ ([`LegendreUnitNorm`](@ref)) is given by

$$
    F_\ell^m(x) \equiv \sqrt{2\pi(2\ell+1) \frac{(\ell-m)!}{(\ell+m)!}} P_\ell^m(x)
$$
