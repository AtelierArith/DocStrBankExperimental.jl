```
struct LegendreSphereNorm <: AbstractLegendreNorm end
```

Trait type denoting the spherical-harmonic normalization of the associated Legendre functions $\lambda_\ell^m(x)$. The spherical-harmonic normalization is defined such that

$$
    \int_{-1}^{1} \left[ \lambda_\ell^m(x) \right]^2 \,dx = \frac{1}{2\pi}
$$

The normalization factor with respect to the standard (unnormalized) Legendre functions $P_\ell^m(x)$ ([`LegendreUnitNorm`](@ref)) is given by

$$
    \lambda_\ell^m(x) \equiv \sqrt{\frac{2\ell+1}{4\pi} \frac{(\ell-m)!}{(\ell+m)!}} P_\ell^m(x)
$$
