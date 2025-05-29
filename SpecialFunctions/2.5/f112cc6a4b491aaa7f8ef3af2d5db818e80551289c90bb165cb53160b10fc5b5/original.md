```
dawson(x)
```

Compute the Dawson function (scaled imaginary error function) of $x$, defined by

$$
\operatorname{dawson}(x)
= \frac{\sqrt{\pi}}{2} e^{-x^2} \operatorname{erfi}(x)
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

This is the accurate version of $\frac{\sqrt{\pi}}{2} e^{-x^2} \operatorname{erfi}(x)$ for large $x$.

External links: [DLMF 7.2.5](https://dlmf.nist.gov/7.2.5), [Wikipedia](https://en.wikipedia.org/wiki/Dawson_function).

See also: [`erfi(x)`](@ref erfi).

# Implementation by

  * `Float32`/`Float64`: C standard math library   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
