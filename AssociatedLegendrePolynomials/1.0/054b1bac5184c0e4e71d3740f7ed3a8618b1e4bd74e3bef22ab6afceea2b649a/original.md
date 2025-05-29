```
struct LegendreUnitNorm <: AbstractLegendreNorm end
```

Trait type denoting the unnormalized associated Legendre functions $P_\ell^m(x)$ which solve the colatitude $\theta$ part of Laplace's equation in spherical coordinates where $x=\cos(\theta)$. The degree $\ell=0$, order $m=0$ constant function is normalized to be unity:

$$
    P_0^0(x) = 1
$$
