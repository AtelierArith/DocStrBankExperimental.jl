```
erfc(x)
```

Compute the complementary error function of $x$, defined by

$$
\operatorname{erfc}(x)
= 1 - \operatorname{erf}(x)
= \frac{2}{\sqrt{\pi}} \int_x^\infty \exp(-t^2) \; \mathrm{d}t
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

This is the accurate version of `1-erf(x)` for large $x$.

External links: [DLMF 7.2.2](https://dlmf.nist.gov/7.2.2), [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Complementary_error_function).

See also: [`erf(x)`](@ref erf).

# Implementation by

  * `Float32`/`Float64`: C standard math library   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: C library for multiple-precision floating-point [MPFR](https://www.mpfr.org/)
