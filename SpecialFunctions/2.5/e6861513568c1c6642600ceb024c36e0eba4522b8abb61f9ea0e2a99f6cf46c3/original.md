```
logerfcx(x)
```

Compute the natural logarithm of the scaled complementary error function of $x$, that is

$$
\operatorname{logerfcx}(x) = \ln(\operatorname{erfcx}(x))
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

This is the accurate version of $\ln(\operatorname{erfcx}(x))$ for large and negative $x$.

External links: [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

See also: [`erfcx(x)`](@ref erfcx).

# Implementation

Based on the [`erfc(x)`](@ref erfc) and [`erfcx(x)`](@ref erfcx) functions.
