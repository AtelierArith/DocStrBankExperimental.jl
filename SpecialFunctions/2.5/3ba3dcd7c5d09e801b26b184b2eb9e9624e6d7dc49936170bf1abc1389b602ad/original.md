```
ellipe(m)
```

Computes Complete Elliptic Integral of 2nd kind $E(m)$ for parameter $m$ given by

$$
\operatorname{ellipe}(m)
= E(m)
= \int_0^{ \frac{\pi}{2} } \sqrt{1 - m \sin^2 \theta} \, \mathrm{d}\theta
\quad \text{for} \quad m \in \left( -\infty, 1 \right] .
$$

External links: [DLMF 19.2.8](https://dlmf.nist.gov/19.2.8), [Wikipedia](https://en.wikipedia.org/wiki/Elliptic_integral#Complete_elliptic_integral_of_the_second_kind).

See also: [`ellipk(m)`](@ref SpecialFunctions.ellipk).

# Arguments

  * `m`: parameter $m$, restricted to the domain $(-\infty,1]$, is related to      the elliptic modulus $k$ by $k^2=m$ and to the modular angle      $\alpha$ by $k=\sin \alpha$.

# Implementation

Using piecewise approximation polynomial as given in [fukushima_2015](@citet)

For $m<0$, followed by [fukushima_2015](@citet).

As suggested in this paper, the domain is restricted to $(-\infty,1]$.
