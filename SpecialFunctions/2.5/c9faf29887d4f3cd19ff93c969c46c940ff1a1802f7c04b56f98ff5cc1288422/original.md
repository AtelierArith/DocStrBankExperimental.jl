```
logerfc(x)
```

Compute the natural logarithm of the complementary error function of $x$, that is

$$
\operatorname{logerfc}(x) = \ln(\operatorname{erfc}(x))
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

This is the accurate version of $\ln(\operatorname{erfc}(x))$ for large $x$.

External links: [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

See also: [`erfcx(x)`](@ref erfcx).

# Implementation

Based on the [`erfc(x)`](@ref erfc) and [`erfcx(x)`](@ref erfcx) functions.
