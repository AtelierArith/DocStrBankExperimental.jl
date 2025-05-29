```
struct LegendreOrthoNorm <: AbstractLegendreNorm end
```

Trait type denoting the orthonormal (full) normalization of the associated Legendre functions $O_\ell^m(x)$. The orthonormal normalization is defined such that

$$
    \int_{-1}^{1} \left[ O_\ell^m(x) \right]^2 \,dx = 1
$$

The normalization factor with respect to the standard (unnormalized) Legendre functions $P_\ell^m(x)$ ([`LegendreUnitNorm`](@ref)) is given by

$$
    O_\ell^m(x) \equiv \sqrt{\frac{2\ell+1}{2} \frac{(\ell-m)!}{(\ell+m)!}} P_\ell^m(x)
$$
