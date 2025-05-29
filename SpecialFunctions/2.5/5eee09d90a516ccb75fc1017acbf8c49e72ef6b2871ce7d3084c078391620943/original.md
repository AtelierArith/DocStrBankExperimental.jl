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

Using the rational approximants tabulated in:

> J. M. Blair, C. A. Edwards, and J. H. Johnson, "Rational Chebyshev approximations for the inverse of the error function", Math. Comp. 30, pp. 827–830 (1976). [https://doi.org/10.1090/S0025-5718-1976-0421040-7](https://doi.org/10.1090/S0025-5718-1976-0421040-7), [http://www.jstor.org/stable/2005402](http://www.jstor.org/stable/2005402)


combined with Newton iterations for `BigFloat`.
