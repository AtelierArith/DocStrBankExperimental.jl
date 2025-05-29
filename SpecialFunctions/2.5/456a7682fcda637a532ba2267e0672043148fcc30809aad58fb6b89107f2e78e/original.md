```
erf(x)
```

Compute the error function of $x$, defined by

$$
\operatorname{erf}(x) = \frac{2}{\sqrt{\pi}} \int_0^x \exp(-t^2) \; \mathrm{d}t
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

External links: [DLMF 7.2.1](https://dlmf.nist.gov/7.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

See also: [`erfc(x)`](@ref erfc), [`erfcx(x)`](@ref erfcx), [`erfi(x)`](@ref erfi), [`dawson(x)`](@ref dawson), [`erfinv(x)`](@ref erfinv), [`erfcinv(x)`](@ref erfcinv).

# Implementation by

  * `Float32`/`Float64`: C standard math library   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: C library for multiple-precision floating-point [MPFR](https://www.mpfr.org/)
