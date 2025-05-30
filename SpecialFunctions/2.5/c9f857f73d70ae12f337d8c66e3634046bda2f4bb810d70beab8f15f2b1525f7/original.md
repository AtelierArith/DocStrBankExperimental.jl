```
erfcinv(x)
```

Compute the inverse error complementary function of a real $x$, that is

$$
\operatorname{erfcinv}(x) = \operatorname{erfc}^{-1}(x)
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

External links: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Inverse_functions).

See also: [`erfc(x)`](@ref erfc).

# Implementation

Using the rational approximants tabulated in [Blair (1976)](@cite blair_1976) combined with Newton iterations for `BigFloat`.
