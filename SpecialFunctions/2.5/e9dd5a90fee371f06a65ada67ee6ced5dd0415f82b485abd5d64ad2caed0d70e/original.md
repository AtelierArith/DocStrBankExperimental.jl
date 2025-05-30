```
erfinv(x)
```

Compute the inverse error function of a real $x$, that is

$$
\operatorname{erfinv}(x) = \operatorname{erf}^{-1}(x)
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

External links: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Inverse_functions).

See also: [`erf(x)`](@ref erf).

# Implementation

Using the rational approximants tabulated in [Blair (1976)](@cite blair_1976) combined with Newton iterations for `BigFloat`.
