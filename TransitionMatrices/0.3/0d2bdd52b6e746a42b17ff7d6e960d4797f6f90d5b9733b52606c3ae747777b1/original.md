A Chebyshev scatterer defined by

$$
r(\theta, \phi)=r_0(1+\varepsilon T_n(\cos\theta))
$$

where $T_n(\cos\theta)=\cos n\theta$.

Attributes:

  * `r₀`: the radius of the base sphere.
  * `ε`: the deformation parameter, which satisfies $-1\le\varepsilon<1$.
  * `n`: the degree of the Chebyshev polynomial.
  * `m`: the relative complex refractive index.
