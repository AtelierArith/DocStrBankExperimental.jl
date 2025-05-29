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

Using piecewise approximation polynomial as given in

> 'Fast Computation of Complete Elliptic Integrals and Jacobian Elliptic Functions', Fukushima, Toshio. (2014). F09-FastEI. Celest Mech Dyn Astr, DOI 10.1007/s10569-009-9228-z, [https://pdfs.semanticscholar.org/8112/c1f56e833476b61fc54d41e194c962fbe647.pdf](https://pdfs.semanticscholar.org/8112/c1f56e833476b61fc54d41e194c962fbe647.pdf)


For $m<0$, followed by

> Fukushima, Toshio. (2014). 'Precise, compact, and fast computation of complete elliptic integrals by piecewise minimax rational function approximation'. Journal of Computational and Applied Mathematics. 282. DOI 10.13140/2.1.1946.6245., [https://www.researchgate.net/publication/267330394](https://www.researchgate.net/publication/267330394)


As suggested in this paper, the domain is restricted to $(-\infty,1]$.
