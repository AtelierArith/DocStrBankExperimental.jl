```
erfi(x)
```

Compute the imaginary error function of $x$, defined by

$$
\operatorname{erfi}(x)
= -i \operatorname{erf}(ix)
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

External links: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Imaginary_error_function).

See also: [`erf(x)`](@ref erf).

# Implementation by

  * `Float32`/`Float64`: C standard math library   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
