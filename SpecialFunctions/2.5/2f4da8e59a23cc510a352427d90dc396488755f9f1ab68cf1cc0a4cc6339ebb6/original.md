```
erfcx(x)
```

Compute the scaled complementary error function of $x$, defined by

$$
\operatorname{erfcx}(x)
= e^{x^2} \operatorname{erfc}(x)
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

This is the accurate version of $e^{x^2} \operatorname{erfc}(x)$ for large $x$. Note also that $\operatorname{erfcx}(-ix)$ computes the Faddeeva function `w(x)`.

External links: [DLMF 7.2.3](https://dlmf.nist.gov/7.2.3), [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Complementary_error_function).

See also: [`erfc(x)`](@ref erfc).

# Implementation by

  * `Float32`/`Float64`: C standard math library   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: MPFR has an open TODO item for this function until then, we use   [DLMF 7.12.1](https://dlmf.nist.gov/7.12.1) for the tail.
